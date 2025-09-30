# Banco API - Testes de Performance com K6

Repositório de testes de performance desenvolvido com a ferramenta [Grafana K6] (https://k6.io/) e escritos em **Javascript**, voltados para a API do sistema bancário.
Repositório: https://github.com/srosanaf/banco-api-performance

---

## 🚀 Introdução

Este projeto tem como objetivo simular diferentes cargas e cenários de uso para a API do banco, avaliando seu desempenho e identificando possíveis gargalos. Os testes são escritos com foco em modularidade, organização por contexto e reutilização de modelos de dados.

---

## 🛠 Tecnologias utilizadas

- [K6](https://k6.io/) - Ferramenta de testes de carga e performance.  
- **Javascript (ES6+)** - Linguagem utilizada para escrever os cenários de teste.  
- [GJSON] (https://github.com/tidwall/gjson) - Para extração de dados em respostas JSON.
- Variáveis de ambiente para configuração dinâmica (ex: `BASE_URL`).

---

## 📂 Estrutura do repositório

```bash
banco-api-performance/
├── helpers/           # Funções utilitárias reutilizáveis para interação com a API
├── fixtures/          # Dados de entrada para testes (ex: usuários, payloads)
├── utils/             # Funções auxiliares e helpers reutilizáveis
├── tests/             # Caso de teste organizados por módulo da API
└── README.md          # Documentação do projeto
└── config/            # Arquivos de configuração de variáveis de ambiente
```

---

## 🎯 Objetivo de cada grupo de arquivos

- **helpers/** → Funções utilitárias reutilizáveis para interação com a API.  
- **fixtures/** → Dados de entrada para testes (ex: usuários, payloads).  
- **utils/** → unções auxiliares e helpers reutilizáveis. 
- **tests/** → Caso de teste organizados por módulo da API.  
- **config/** → Arquivos de configuração de variáveis de ambiente.

---

## ⚙️ Modo de instalação e execução do projeto

### 1. Clonar o repositório
```bash
git clone https://github.com/srosanaf/banco-api-performance.git
cd banco-api-performance
```

### 2. Instalar dependências
```bash
npm install
```

### 3. Configure as variáveis de ambiente

Altere o arquivo `config.local.json` e defina a URL base da API a ser testada:
```json
{
    "baseUrl": "http://localhost:3000"  
}
```
Essas variáveis serão utilizadas dinamicamente nos testes para montar as requisições.

### 4. Executar testes com K6
Exemplo de execução simples:
```bash
k6 run tests/login.test.js
```
Certifique-se de passar a variável de ambiente `BASE_URL` caso não esteja usando um `config.local.json` ou uma abordagem de carregamento automático:

```bash
k6 run tests/autenticacao/login.test.js -e BASE_URL=http://localhost:3000
```

### 5. Relatórios em tempo real e exportação
Você pode ativar o modo dashboard do K6 e exportar o relatório ao final do teste:

```bash
K6_WEB_DASHBOARD=true \ K6_WEB_DASHBOARD_EXPORT=html-report.html \ k6 run tests/autenticacao/login.test.js \ -e BASE_URL=http://localhost:3000
```
O relatório será salvo no arquivo `html-report.html` após a execução.

---
