# 🤖 Automação de Tarefas e Monitoramento com n8n

Sistema de automação desenvolvido para centralizar o monitoramento de 
infraestrutura e a gestão de tarefas da equipe de TI, integrando 
Telegram, Notion e Uptime Kuma.

## 🎯 O problema

A equipe não recebia notificações centralizadas sobre:
- Status dos serviços de infraestrutura (internet, sistemas, firewalls)
- Tarefas pendentes e prazos
- Criação e conclusão de tarefas

## 💡 A solução

Construí um sistema de automação com **n8n** rodando em **Docker** que:

1. **Monitora a infraestrutura** 5x ao dia e envia relatórios no Telegram
2. **Gerencia tarefas** através de comandos no Telegram (`/nova`, `/ok`, `/lista`)
3. **Integra com o Notion** para armazenar as tarefas
4. **Envia lembretes diários** das tarefas que vencem no dia seguinte

## 🛠️ Stack Técnica

| Tecnologia | Uso |
|---|---|
| **n8n** | Orquestração dos workflows |
| **Docker + Docker Compose** | Deploy e isolamento |
| **Linux (Ubuntu Server)** | Infraestrutura |
| **Telegram Bot API** | Interface do usuário |
| **Notion API** | Banco de dados de tarefas |
| **Uptime Kuma API** | Monitoramento de serviços |

## 🏗️ Arquitetura

<pre>
Telegram (usuário)
    ↓
n8n (workflows)
    ├── /nova  → Notion (criar tarefa)
    ├── /ok    → Notion (concluir tarefa)
    ├── /lista → Notion (listar pendentes)
    └── schedule → Uptime Kuma → Telegram (relatório)
</pre>


## 📋 Comandos disponíveis

| Comando | Função |
|---|---|
| `/nova Nome \| DD/MM/AAAA` | Cria uma nova tarefa |
| `/ok ID` | Marca a tarefa como concluída |
| `/lista` | Lista todas as tarefas pendentes |

## 📁 Workflows

| Arquivo | Descrição |
|---|---|
| `workflows/gestao-tarefas.json` | Criação, conclusão e listagem de tarefas |
| `workflows/aviso-diario.json` | Lembrete diário de tarefas |
| `workflows/monitoramento.json` | Relatório de status da infraestrutura |

## 🚀 Como usar

1. Importe os arquivos `.json` no seu n8n
2. Configure as credenciais:
   - **Telegram**: token do bot (@BotFather)
   - **Notion**: integração interna
3. Substitua os placeholders (`SEU_CHAT_ID`, `SEU_DATABASE_ID`, etc.)
4. Ative os workflows

## 📸 Screenshots

*(Adicione aqui prints dos comandos no Telegram e dos workflows no n8n)*

## 🎓 Aprendizados

- Configuração de n8n com Docker em servidor Linux
- Integração com APIs REST (Telegram, Notion, Uptime Kuma)
- Programação em JavaScript nos nós Code
- Tratamento de erros e persistência de dados
- Configuração de fuso horário em containers

## 👤 Autor

**Rafael de Freitas**
- GitHub: [@rffino74](https://github.com/rffino74)
