# Desafio Técnico para Vaga Backend - Node.js

## Objetivo

Desenvolver uma API para gerenciamento de tarefas (To-Do List) utilizando Node.js, Fastify, TypeScript e PostgreSQL, seguindo os princípios de Arquitetura Limpa (Clean Architecture).

## Descrição

Você deve criar uma API RESTful que permita criar, ler, atualizar e deletar tarefas. As tarefas devem conter as seguintes informações:

- ID (UUID)
- Título (string)
- Descrição (string)
- Status (enum: 'pendente', 'em progresso', 'concluído')
- Data de criação (timestamp)
- Data de atualização (timestamp)

Além disso, a API deve implementar autenticação utilizando JWT (JSON Web Token) e a criação de senhas deve ser feita usando a biblioteca `bcryptjs`.

## Requisitos

- Utilizar Node.js com Fastify
- Escrever o código em TypeScript
- Usar PostgreSQL para armazenamento dos dados
- Seguir os princípios de Clean Architecture
- Implementar autenticação JWT
- Utilizar a biblioteca `bcryptjs` para gerenciamento de senhas

## Diferencial
- Escrever testes unitários com JEST

## Funcionalidades

A API deve fornecer os seguintes endpoints:

### Registro de usuário

- **URL**: `/auth/register`
- **Método**: `POST`
- **Corpo da Requisição**:
  ```json
  {
    "username": "nome_de_usuario",
    "password": "senha_segura"
  }
  ```
- **Resposta**:
  ```json
  {
    "message": "Usuário registrado com sucesso"
  }
  ```

### Login de usuário

- **URL**: `/auth/login`
- **Método**: `POST`
- **Corpo da Requisição**:
  ```json
  {
    "username": "nome_de_usuario",
    "password": "senha_segura"
  }
  ```
- **Resposta**:
  ```json
  {
    "token": "jwt_token"
  }
  ```

### Criar uma nova tarefa

- **URL**: `/tasks`
- **Método**: `POST`
- **Cabeçalho**: `Authorization: Bearer jwt_token`
- **Corpo da Requisição**:
  ```json
  {
    "title": "Título da tarefa",
    "description": "Descrição da tarefa",
    "status": "pendente"
  }
  ```
- **Resposta**:
  ```json
  {
    "id": "uuid",
    "title": "Título da tarefa",
    "description": "Descrição da tarefa",
    "status": "pendente",
    "createdAt": "timestamp",
    "updatedAt": "timestamp"
  }
  ```

### Obter todas as tarefas com paginação

- **URL**: `/tasks`
- **Método**: `GET`
- **Cabeçalho**: `Authorization: Bearer jwt_token`
- **Parâmetros de Consulta**:
  - `page` (opcional, número inteiro, default: 1) - Número da página
  - `limit` (opcional, número inteiro, default: 10) - Número de tarefas por página
- **Resposta**:
  ```json
  {
    "tasks": [
      {
        "id": "uuid",
        "title": "Título da tarefa",
        "description": "Descrição da tarefa",
        "status": "pendente",
        "createdAt": "timestamp",
        "updatedAt": "timestamp"
      },
    ],
    "pagination": {
        "page": 1,
        "limit": 10,
        "totalPages": 1,
        "totalTasks": 1
    }
  }
  ```

### Obter uma tarefa pelo ID

- **URL**: `/tasks/:id`
- **Método**: `GET`
- **Cabeçalho**: `Authorization: Bearer jwt_token`
- **Resposta**:
  ```json
  {
    "id": "uuid",
    "title": "Título da tarefa",
    "description": "Descrição da tarefa",
    "status": "pendente",
    "createdAt": "timestamp",
    "updatedAt": "timestamp"
  }
  ```

### Atualizar uma tarefa

- **URL**: `/tasks/:id`
- **Método**: `PUT`
- **Cabeçalho**: `Authorization: Bearer jwt_token`
- **Corpo da Requisição**:
  ```json
  {
    "title": "Novo título da tarefa",
    "description": "Nova descrição da tarefa",
    "status": "em progresso"
  }
  ```
- **Resposta**:
  ```json
  {
    "id": "uuid",
    "title": "Novo título da tarefa",
    "description": "Nova descrição da tarefa",
    "status": "em progresso",
    "createdAt": "timestamp",
    "updatedAt": "timestamp"
  }
  ```

### Deletar uma tarefa

- **URL**: `/tasks/:id`
- **Método**: `DELETE`
- **Cabeçalho**: `Authorization: Bearer jwt_token`
- **Resposta**:
  ```json
  {
    "message": "Tarefa deletada com sucesso"
  }
  ```

## Estrutura do Projeto

Organize o projeto seguindo os princípios de Clean Architecture.

## Critérios de Avaliação

- **Funcionalidade**: A API deve atender a todos os requisitos funcionais.
- **Código**: Clareza, organização, uso adequado de TypeScript e adoção de boas práticas de codificação.
- **Arquitetura**: Aderência aos princípios de Clean Architecture.
- **Documentação**: Qualidade da documentação da API.

## Como Enviar

1. Faça um fork deste repositório.
2. Implemente a solução no seu fork.
3. Envie um email para: `contato@wecodecds.com` com o link do seu repositório.

Você terá 72 horas para entregar o desafio, contadas a partir da entrega deste desafio a você.

> Inteligência é a capacidade de se adaptar a mudança - Stephen Hawking

Boa sorte!