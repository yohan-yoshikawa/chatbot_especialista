# EducaReserve — Chatbot com Google Gemini

## 1. Descrição do projeto

O EducaReserve é um chatbot especialista desenvolvido para responder perguntas sobre a reserva de equipamentos eletrônicos de uma escola fictícia, a Escola ABC.

O conhecimento utilizado pelo chatbot é inserido diretamente no contexto do modelo. Dessa forma, o bot deve responder somente com base nas informações fornecidas no contexto e informar quando não possuir uma informação, evitando inventar equipamentos, reservas, horários ou regras.

O projeto foi desenvolvido com Python, Google Gemini e Panel, tendo como referência o exemplo de chatbot do curso **ChatGPT Prompt Engineering for Developers**, da DeepLearning.AI.

### Funcionamento

O chatbot possui três elementos principais no contexto:

- **Personalidade:** atendente educado, objetivo e profissional.
- **Objetivo/tarefa:** responder dúvidas de professores sobre disponibilidade e regras de reserva.
- **Conhecimento:** equipamentos, horários, turmas, reservas existentes e regras da Escola ABC.

A conversa é limitada a **três perguntas**. Depois da terceira resposta, o chatbot deve apresentar um breve resumo das perguntas e respostas e encerrar a conversa.

## 2. Tecnologias utilizadas

- Python
- Google Gemini API
- Google GenAI SDK
- Panel
- python-dotenv
- Jupyter Notebook / Google Colab

## 3. Estrutura do projeto

```text
ProjetoChatBot/
├── ProjetoChatBot.ipynb
├── .env
├── env.example
├── .gitignore
└── README.md
```

> O arquivo `.env` é local e contém a chave real da API. Ele está incluído no `.gitignore` e **não deve ser enviado ao GitHub**.

## 4. Configuração da API

### 4.1 Criar a chave da API

Crie uma chave de API do Google Gemini no Google AI Studio.

### 4.2 Criar o arquivo `.env`

Na raiz do projeto, faça uma cópia do `env.example` e renomeie para:

```text
.env
```

Depois, coloque sua chave:

```env
GEMINI_KEY=sua_chave_real_aqui
```

Não compartilhe essa chave e não a publique no GitHub.

## 5. Instalação das dependências

No ambiente Python utilizado para executar o projeto, instale:

```bash
pip install google-genai python-dotenv panel
```

Se estiver usando o Google Colab, execute em uma célula:

```python
!pip install google-genai python-dotenv panel
```

## 6. Execução

1. Clone ou baixe este repositório.
2. Crie o arquivo `.env` conforme explicado acima.
3. Instale as dependências.
4. Abra o arquivo `ProjetoChatBot.ipynb`.
5. Execute as células na ordem.
6. A interface do EducaReserve será exibida no notebook.
7. Faça até três perguntas relacionadas às informações da Escola ABC.

### Perguntas utilizadas na demonstração

1. Quantos notebooks estão disponíveis no dia 20/09 das 08h às 10h?
2. Posso reservar 15 notebooks nesse horário para uma turma?
3. E das 10h às 12h?

Após a terceira resposta, o chatbot deve apresentar o resumo da conversa e encerrá-la.

## 7. Exemplo de conhecimento disponível

O contexto do chatbot contém, entre outras informações:

- 30 tablets;
- 20 notebooks;
- 5 projetores;
- funcionamento de segunda a sexta, das 07:00 às 18:00;
- turmas cadastradas;
- reservas realizadas nos dias 20/09/2026 e 21/09/2026;
- regras para verificar disponibilidade;
- limite de três perguntas.

## 8. Segurança

A chave da API é carregada por meio da variável de ambiente `GEMINI_KEY`:

```python
from dotenv import load_dotenv
import os

load_dotenv()

GEMINI_KEY = os.getenv("GEMINI_KEY")
```

O arquivo `.env` está listado no `.gitignore` para evitar que a chave seja enviada ao repositório.

O arquivo `env.example` contém somente o nome do parâmetro, sem o valor secreto:

```env
GEMINI_KEY=
```

## 9. Objetivo acadêmico

O projeto demonstra como um LLM pode ser configurado como um chatbot especialista utilizando um contexto específico, limitando o conhecimento disponível ao modelo e orientando seu comportamento por meio de instruções.

A implementação também adapta o exemplo de chatbot do curso da DeepLearning.AI para utilizar o Google Gemini como provedor do LLM.
