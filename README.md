# 🔍 Multi-Agent Research System

An autonomous multi-agent pipeline that researches any topic end-to-end — from web search to a structured, critic-reviewed report. Built with LangChain, LangGraph, and local LLMs via Ollama.

## 🧠 How It Works

The pipeline runs 4 sequential agents, each with a distinct role:
[Search Agent] → [Reader Agent] → [Writer Chain] → [Critic Chain]

1. **Search Agent** — Uses Tavily to find recent, reliable sources on the given topic
2. **Reader Agent** — Picks the most relevant URL and scrapes its full content using multi-strategy extraction (trafilatura → readability → BeautifulSoup fallback)
3. **Writer Chain** — Synthesizes search results and scraped content into a structured research report
4. **Critic Chain** — Reviews the report and returns a score, strengths, areas to improve, and a one-line verdict

## 🗂️ Project Structure
Multi-Agent-Research-System/
│
├── src/
│   ├── agents/
│   │   └── agents.py          # Search and reader agent definitions
│   ├── tools/
│   │   └── tools.py           # web_search and scrape_url tools
│   └── pipelines/
│       └── pipeline.py        # Main pipeline orchestration
│
├── main.py                    # Entry point
├── app.py                     # (Streamlit UI - optional)
├── requirements.txt
└── .env                       # API keys (not committed)

## ⚙️ Setup

### 1. Clone the repository
```bash
git clone https://github.com/ratul-podder99/Multi-Agent-Research-System.git
cd Multi-Agent-Research-System
```

### 2. Create and activate a virtual environment
```bash
python -m venv venv
source venv/bin/activate        # macOS/Linux
venv\Scripts\activate           # Windows
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

### 4. Set up environment variables

Create a `.env` file in the root directory:
```env
TAVILY_API_KEY=your_tavily_api_key_here
```

Get your free Tavily API key at [tavily.com](https://tavily.com)

### 5. Pull and run the LLM locally via Ollama

Install [Ollama](https://ollama.com) then pull a tool-capable model:
```bash
ollama pull mistral-nemo
```

## 🚀 Usage

Edit the topic in `main.py`:
```python
topic = "Effects of AI on the job market 2026"
run_research_pipeline(topic)
```

Then run:
```bash
python main.py
```

## 🛠️ Tech Stack

| Component | Technology |
|---|---|
| LLM (local) | Ollama + Mistral-Nemo |
| Agent framework | LangChain  |
| Web search | Tavily |
| Web scraping | trafilatura, readability-lxml, BeautifulSoup4 |
| Environment | python-dotenv |
| UI (optional) | Streamlit |

## 📋 Requirements

- Python 3.10+
- [Ollama](https://ollama.com) installed and running locally
- Tavily API key (free tier available)

## 📄 License

This project is licensed under the Apache 2.0 License — see the [LICENSE](LICENSE) file for details.