


# CRUD de Clientes - Spring Boot

O objetivo do projeto é construir uma API REST com as operações básicas de CRUD, seguindo boas práticas como separação em camadas, tratamento de exceções e validações.

## Funcionalidades

A API permite as seguintes operações sobre o recurso "clientes":

- Busca paginada de clientes  
- Busca de cliente por ID  
- Inserção de novo cliente  
- Atualização de cliente existente  
- Deleção de cliente  

## Especificações Técnicas

- Linguagem: Java 21
- Framework: Spring Boot
- Gerenciador de dependências: Maven
- Banco de dados: H2 (em memória)
- Validações: Bean Validation (Jakarta)
- Testes via Postman

## Entidade

A entidade `Client` possui os seguintes atributos:

- `id` (Long)
- `name` (String) - obrigatório
- `cpf` (String)
- `income` (Double)
- `birthDate` (LocalDate) - não pode ser futura
- `children` (Integer)

![image](https://github.com/user-attachments/assets/a59c883f-94bf-42d6-924c-c98560f27a02)


## Validações

- `name`: não pode ser vazio  
- `birthDate`: não pode ser uma data futura (`@PastOrPresent`)  
- Erros de validação retornam status HTTP 422 com mensagens customizadas

## Tratamento de Erros

- ID não encontrado: retorna HTTP 404 (Not Found)
- Dados inválidos: retorna HTTP 422 (Unprocessable Entity)

## Endpoints

### Buscar cliente por ID

```
GET /clients/{id}
```

### Buscar clientes paginados

```
GET /clients?page=0&size=6
```

### Inserir novo cliente

```
POST /clients
{
  "name": "Maria Silva",
  "cpf": "12345678901",
  "income": 6500.0,
  "birthDate": "1994-07-20",
  "children": 2
}
```

### Atualizar cliente existente

```
PUT /clients/{id}
{
  "name": "Maria Silvaaa",
  "cpf": "12345678901",
  "income": 6500.0,
  "birthDate": "1994-07-20",
  "children": 2
}
```

### Deletar cliente

```
DELETE /clients/{id}
```



## Como Executar

```bash
git clone https://github.com/seu-usuario/seu-repositorio.git
cd seu-repositorio
./mvnw spring-boot:run
```

Acesse a aplicação em: `http://localhost:8080/clients`


