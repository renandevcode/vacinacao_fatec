# Assistente de Vacinação - Bot Telegram

Este projeto é um assistente virtual no Telegram que consulta o calendário de vacinação oficial do Ministério da Saúde, permitindo buscas por grupo ou idade. A lógica faz o mapeamento de idades em subperíodos e grupos, fornecendo as vacinas disponíveis para cada faixa.

## Funcionalidades

- Busca de vacinas por grupo (Criança, Adolescente, Adulto, Idoso, Gestante).
- Busca de vacinas por idade, mapeando subfaixas (em meses ou anos).
- Coleta de dados diretamente do site oficial via scraping.
- Respostas em formato amigável com markdown, destacando grupos e períodos.

## Pré-requisitos

- Python 3.10 ou superior.
- Bibliotecas: telebot, requests, bs4 (BeautifulSoup), python-dotenv.
- Token do bot Telegram (armazenado em uma variável de ambiente `.env`).

## Funções

### 1. scrap(grupo_id, periodo)

Responsável por fazer o scraping no site do Ministério da Saúde. Recebe o `grupo_id` (identificador do grupo) e, opcionalmente, uma lista de subperíodos. Ela extrai as vacinas e períodos do site e retorna uma lista com as informações.

### 2. formatar_mensagem_bot(dados_json)

Recebe a lista de vacinas (em formato JSON) e formata uma mensagem amigável, agrupando por grupo e período. Retorna um texto que pode ser enviado no chat.

### 3. Handlers do Telegram

- **start e help**: Iniciam o bot e fornecem opções básicas de navegação.
- **Início**: Responde ao usuário com uma mensagem explicando o papel do bot.
- **Help**: Oferece links ou informações extras de suporte.
- **Vacinas**: Pergunta ao usuário se a busca será por grupo ou idade.
- **Idade**: Solicita a data de nascimento e, com base na idade, determina o grupo e subfaixa.
- **fornece_grupo**: Oferece as opções de grupos diretamente, sem a necessidade de idade.

## Como usar

1. Inicie o bot com o comando `/start`.
2. Escolha entre as opções 'Vacinas' ou 'Help'.
3. Se escolher 'Vacinas', decida se quer buscar por grupo ou idade.
   - Caso escolha idade, informe a data de nascimento, e o bot retornará o grupo e as vacinas correspondentes.
   - Caso escolha grupo, selecione o grupo, e o bot retorna as vacinas desse grupo.

## Variáveis de Ambiente

O token do bot deve ser armazenado em um arquivo `.env` no mesmo diretório do script. A variável deve ser nomeada como `TOKEN_BOT`.
