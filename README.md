# 🔬 Research Paper Analyst
### Prompt Engineering with LangChain & Google Gemini

A mini-project that uses **Google Gemini** as an AI expert and **LangChain** for prompt orchestration to intelligently transform and summarise a research paper abstract for different target audiences — automatically adapting tone, depth, and structure based on who's reading.

---

## 📌 Project Overview

This project demonstrates how **prompt engineering** and **multi-turn conversational chains** can be used to extract meaningful insights from academic research. It takes a research paper abstract on **Ethics of Generative AI in Healthcare** and generates three distinct reports tailored to three different audiences, all from a single LLM chain.

---

## 🎯 Use Case

The research paper analysed in this project is a **systematic scoping review** on ethical considerations of Generative AI in healthcare, covering:

- 193 articles across text, image, and structured data modalities
- 10 core ethical principles (non-maleficence, equity, privacy, etc.)
- GANs, LLMs, autoencoders, and diffusion models for data synthesis

The project uses **multi-turn memory** — each subsequent LLM call includes the full conversation history — to progressively refine and restructure reports without re-processing the paper.

---

## ⚙️ Tech Stack

| Component | Technology |
|-----------|------------|
| **LLM** | Google Gemini (`gemini-flash-latest`) |
| **LLM Framework** | LangChain (`v0.1.19`) |
| **Gemini Binding** | `langchain-google-genai` (`v0.0.11`) |
| **Prompt Orchestration** | LangChain Expression Language (LCEL) |
| **Interface** | Jupyter Notebook |
| **Language** | Python 3 |

---

## 🚀 Workflow

```
Research Paper Abstract
        │
        ▼
┌─────────────────────────────┐
│   System Prompt (AI Expert)  │
│   + ChatPromptTemplate       │
└────────────┬────────────────┘
             │
             ▼
     LCEL Chain: Prompt | Gemini
             │
   ┌─────────┴──────────────────────────┐
   │                                    │
   ▼                                    ▼
Report 1                           Report 2 & 3
(General Audience,              (Multi-turn, healthcare
 ≤10 lines summary)              & GenAI company reports)
```

### Step-by-Step

1. **Install dependencies** — `langchain`, `langchain-google-genai`, `langchain-community`
2. **API Authentication** — Securely enter the Gemini API key via `getpass`
3. **Initialise Gemini LLM** — Load `gemini-flash-latest` with temperature = 0.1 and streaming enabled
4. **Define Prompt Template** — System prompt sets Gemini to behave as an AI expert; user instructions drive the transformation
5. **Build LCEL Chain** — `prompt | gemini` pipeline
6. **Generate Report 1** — 10-line plain-language summary for a general audience
7. **Generate Report 2** — Detailed report for a **healthcare company**, including bullet points on pros & cons of ethics in Generative AI
8. **Generate Report 3** — Detailed report for a **Generative AI company** in healthcare, with sections on text, image, and structured data modalities

---

## 📂 Output Reports

| Report | Audience | Format |
|--------|----------|--------|
| **Report 1** | General Public | 10-line concise summary |
| **Report 2** | Healthcare Company | Detailed report + Ethics Pros/Cons bullet points |
| **Report 3** | GenAI Healthcare Company | Detailed report + Key points by data modality |

---

## 🔑 Prerequisites

- Python 3.8+
- A valid [Google Gemini API Key](https://aistudio.google.com/)
- Jupyter Notebook or JupyterLab

---

## 📦 Installation

```bash
pip install langchain==0.1.19
pip install langchain-google-genai==0.0.11
pip install langchain-community==0.0.38
```

---

## ▶️ Running the Project

1. Open `Research_Paper_Analyst.ipynb` in Jupyter Notebook
2. Run all cells sequentially
3. When prompted, enter your **Gemini API Key**
4. (Optional) Run the model listing cell to see available Gemini models and update the model name if needed
5. View the three generated reports printed in the notebook

---

## 🧠 Key Concepts Demonstrated

- **Prompt Engineering** — Crafting a system persona and user-instruction-driven prompt template
- **LangChain Expression Language (LCEL)** — Composable, readable chain syntax (`prompt | llm`)
- **Multi-turn Conversation Memory** — Appending previous responses to the `messages` list to maintain context across LLM calls
- **Audience-Adaptive Text Generation** — Same source abstract → radically different outputs based on instruction

---

## 📄 Research Paper

> *"Ethics of Generative AI in Healthcare: A Systematic Scoping Review"*
> — A review of 2,859 articles (Jan 2013 – Jul 2023) from four academic databases, analysing ethical issues caused by and resolved through Generative AI across text, image, and structured healthcare data modalities.

---

## 📁 Project Structure

```
Research_Paper_Analyst/
│
├── Research_Paper_Analyst.ipynb   # Main notebook
└── README.md                      # Project documentation
```

---

## 📝 Notes

- The model is initialised with `temperature=0.1` for consistent, focused outputs
- `convert_system_message_to_human=True` ensures compatibility with Gemini's message format
- The project uses `streaming=True` for real-time token-level output during generation

---

## 🏷️ Tags

`LangChain` · `Google Gemini` · `Prompt Engineering` · `LCEL` · `GenAI` · `Healthcare AI` · `NLP` · `Jupyter Notebook` · `Multi-turn Conversation`
