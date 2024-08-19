<h1>
    <img align="center" width="40px" src="./docker-mark-blue.svg" alt="Docker logo">
    <span>Provisionando uma API no Dokcer</span>
</h1>

Repositório desenvolvido para fins educativos.

## Objetivo

Criar e executar o Docker Compose buildando o Dockerfile para realizar as seguintes tarefas:

- Criar um Dockerfile da API de cadastro (https://github.com/fraigo/node-express-rest-api-example)
    
- Usar a imagem do node:14

- Criar um Docker Compose com build para imagem da API
    
- Mapear a porta 8080

## Exemplo de Dockerfile

```
FROM node:14

WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 8000
CMD ["npm", "run", "start"]
```

## Exemplo de Docker Compose

```
version: '3.8'

services:
  api:
    build:
      context: .
      dockerfile: Dockerfile
    ports:
      - "8080:8000"
```

## Estrutura do projeto

Certifique-se de que o projeto tenha a seguinte estrutura:

```
.
└── node-express-rest-api-example
    ├── database.js
    ├── docker-compose.yml
    ├── Dockerfile
    ├── express-api-test.postman_collection.json
    ├── package.json
    ├── package-lock.json
    ├── README.md
    ├── server.js
    └── test.json
```

## Instruções do Dockerfile e o Docker Compose

### Execute o contêiner

No diretório onde estão o Dockerfile e o arquivo docker-compose.yml, execute:

```
sudo docker-compose up --build -d
```
