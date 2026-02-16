# DevOps Lab - Nginx com Docker

Projeto de laboratório para prática de containerização.

## Tecnologias
- Docker
- WSL2
- Nginx
- Windows + PowerShell

## Instalação do ambiente

Foi configurado um ambiente local para execução de containers em Windows, utilizando Docker integrado ao Linux via WSL2.

Componentes instalados

- Docker Desktop
- WSL2 (Windows Subsystem for Linux)
- Distribuição Linux (Ubuntu)
- Docker Engine (via Docker Desktop)
- Docker Compose (incluso no Docker Desktop)

## O que foi feito

Após instalação docker realizei a configuração do Docker Desktop e integração com WSL2 via PowerShell:
```bash
       wsl --update
       wsl --shutdown
```

Teste inicial do funcionamento do Docker: 
```bash
       docker run hello-world
``` 

Verificação dos containers ativos: 
```bash
       docker ps
```

Execução de um container Nginx:
```bash
       docker run -d -p 8080:80 nginx
```
O que isso faz: 
- -d: roda em segundo plano
- -p: 8080:80 expõe a porta
- nginx: servidor web

Aplicação publicada em: 
```bash
       http://localhost:8080
```

- Criação de Dockerfile personalizado
Criação da pasta do projeto: 
```bash
       mkdir C:\Sites\devops-lab
       cd C:\Sites\devops-lab
```
Criação do Dockerfile
```bash
       New-Item Dockerfile -ItemType File
```
Dentro do arquivo Dockerfile foi acidionado o caminho: 
```bash
       FROM nginx:latest
       COPY index.html /usr/share/nginx/html/index.html
```
Continuando na mesma pasta devops-lab criei o arquivo:

index.html

Conteúdo: 
```bash
       <!DOCTYPE html>
<html>
<head>
    <title>DevOps Lab - Willamis</title>
</head>
<body>
    <h1>Projeto DevOps</h1>
    <p>Container Nginx rodando com Docker</p>
    <p>Autor: Willamis Silva</p>
</body>
</html>

```

Troubleshooting de conflitos de porta
Pare o serviço do container utilização padrão do nginx, executei o comando de para do container:

```bash
       docker stop <container_id>
```

Buid da imagem customizada: 
```bash
       docker build -t nginx-will .
```

Execução do container:
```bash
    docker run -d -p 8080:80 nginx-will
```
Aplicação web publicada em container Docker com imagem personalizada: 

```bash
       http://localhost:8080
```

O que este laboratório demonstra: 

- Instalação e configuração de ambiente Docker em Windows
- Integração com WSL2
- Criação de imagens via Dockerfile
- Execução e gerenciamento de containers
- Mapeamento de portas
- Troubleshooting de conflitos de rede
- Publicação de aplicação web containerizada
- Ambiente reproduzível local (Infraestrutura como Código – nível básico)
