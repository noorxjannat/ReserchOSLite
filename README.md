# 🔬 ResearchPilot AI

[![Hacktoberfest](https://img.shields.io/badge/Hacktoberfest-2024%2F2025-orange.svg?style=flat-square&logo=github)](https://hacktoberfest.com/)
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg?style=flat-square)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.11%2B-blue.svg?style=flat-square&logo=python)](https://python.org)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.115%2B-009688.svg?style=flat-square&logo=fastapi)](https://fastapi.tiangolo.com)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.39%2B-FF4B4B.svg?style=flat-square&logo=streamlit)](https://streamlit.io)
[![Tests](https://img.shields.io/badge/Tests-22%20Passed-brightgreen.svg?style=flat-square&logo=pytest)](tests/)

> **"An Autonomous Multi-Agent Research Workflow Assistant"**  
> Moving students, researchers, and scientific labs from a raw idea to a structured, publication-ready research blueprint.

---

## 📌 1. Project Overview

**ResearchPilot AI** is an open-source, modular multi-agent scientific workspace. Rather than serving as a generic conversational chatbot, ResearchPilot AI simulates a **virtual research assistant team** (Research Director, Topic Modeler, Literature Analyst, Research Gap Detector, Methodology Designer, Empirical Data Scientist, and Publication Blueprint Compiler).

The platform guides researchers through the cognitive pipeline of early-stage discovery:
1. Research topic understanding & taxonomy
2. Live literature discovery (arXiv & Semantic Scholar)
3. Literature synthesis & extraction
4. Research gap white-space discovery
5. Formal research questions (RQs) & hypothesis generation
6. Methodology & experimental design
7. Empirical dataset profiling & machine learning baselines
8. Publication-ready research proposal blueprint generation (Markdown & LaTeX export)

---

## 💥 2. Problem Statement

Beginning researchers—especially undergraduate thesis candidates, MSc students, and doctoral scholars—frequently face significant cognitive hurdles:
- **Broad, Unfocused Inquiries**: Inability to decompose a high-level curiosity into tractable scientific questions.
- **Literature Overload**: Difficulty isolating dominant methodology paradigms, standard benchmark datasets, and prevailing limitations across hundreds of papers.
- **Unclear Research Gaps**: Vague problem statements that fail to clearly delineate existing approaches from novel contributions.
- **Non-Standardized Evaluation**: Selecting arbitrary metrics that do not conform to discipline-specific standards.

**ResearchPilot AI bridges this gap** by enforcing structured academic rigor, domain plugin validation, and reproducible empirical analysis.

---

## 🏛️ 3. Architecture & Multi-Agent Workflow

```
+-----------------------------------------------------------------------------------------+
|                                    User Research Idea                                   |
+-----------------------------------------------------------------------------------------+
                                             │
                                             ▼
+-----------------------------------------------------------------------------------------+
|                                 Research Director Agent                                 |
|                       (StateGraph orchestrator & workflow telemetry)                    |
+-----------------------------------------------------------------------------------------+
       │                  │                  │                  │                  │
       ▼                  ▼                  ▼                  ▼                  ▼
+--------------+   +--------------+   +--------------+   +--------------+   +--------------+
| Topic Agent  |──>| Literature   |──>|  Gap Agent   |──>| Methodology  |──>| Report Agent |
| (Taxonomy &  |   | Agent        |   | (White-space |   | Agent (Study |   | (Structured  |
| Challenges)  |   | (arXiv + S2) |   |  Synthesis)  |   |  Protocols)  |   |  Blueprint)  |
+--------------+   +--------------+   +--------------+   +--------------+   +--------------+
                                                                                   ▲
                                                                                   │
                                      +────────────────────────────────────────────+
                                      │ Empirical Data Agent & Scientific RAG
                                      │ (Descriptive Stats, ML Models, PDF QA)
```

### Core Architectural Principles
1. **Domain-Agnostic Core + Domain Plugin Architecture**:
   - Agnostic orchestrator that dynamically integrates with scientific plugins:
     - `domains/cse/`: Computer Science & AI (Complexity splits, VRAM footprint, F1, Latency, FLOPs).
     - `domains/eee/`: Electrical Engineering (IEEE 519 THD compliance, Power Loss, Efficiency).
     - `domains/genetics/`: Genetic Engineering (Volcano classification, Replicate power, log2FC, FDR).
     - Easily expandable to *Agriculture*, *Medicine*, and *Chemistry*.
2. **Provider-Agnostic LLM Layer**:
   - Universal adapter supporting **Google Gemini API**, **OpenAI API**, and an intelligent **Mock Scientific Engine** for zero-cost offline development and testing.
3. **Scientific Document RAG**:
   - Ingestion of research papers (PDF/TXT), sentence-level chunking, cosine vector store, and grounded retrieval.
4. **Empirical Data Lab**:
   - Automated profiling of uploaded or benchmark CSV datasets: Pearson correlation matrices, Random Forest & Gradient Boosting models, feature importance, and peer-reviewed scientific prose.

---

## ✨ 4. Key Features

- **Autonomous Multi-Agent Collaboration**: 6 specialized agents running in coordinated state sequence.
- **Multi-Source Literature Mining**: Queries live arXiv XML feed and Semantic Scholar Graph API.
- **Interactive Scientific RAG**: Grounded question answering (e.g., *"According to previous studies, what methods are commonly used?"*).
- **Domain Plugin System**: Plug-and-play evaluation metrics and computational tools for different fields.
- **Empirical Machine Learning Engine**: Automated classification and regression benchmarks with Scikit-learn.
- **Interactive Plotly Visualizations**: Distribution histograms, bivariate scatter plots, correlation heatmaps, and RNA-Seq volcano plots.
- **Publication-Ready Export**: One-click download of research blueprints in formatted **Markdown (.md)** and publication-ready **LaTeX (.tex)** formats.

---

## ⚡ 5. Installation & Setup

### Prerequisites
- Python 3.11+
- Git

### 1. Clone Repository
```bash
git clone https://github.com/your-username/ResearchPilot-AI.git
cd ResearchPilot-AI
```

### 2. Create Virtual Environment
```bash
python -m venv .venv
# On Windows:
.venv\Scripts\activate
# On Linux / macOS:
source .venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Configure Environment
```bash
cp .env.example .env
# Edit .env to supply your Gemini or OpenAI API key (optional for offline testing)
```

---

## 🚀 6. Usage & Launching

### Start the Streamlit Scientific Dashboard
```bash
python run.py --frontend
# Or directly:
streamlit run app.py
```
Open your browser at `http://localhost:8501`.

### Start the FastAPI Backend REST API
```bash
python run.py --backend
# Access Interactive Swagger Docs at: http://127.0.0.1:8000/api/docs
```

### Start Both Concurrently
```bash
python run.py --all
```

---

## 🧪 7. Test Suite

ResearchPilot AI includes a comprehensive Pytest test suite covering agents, data analysis, paper search, domain plugins, and REST endpoints:

```bash
python -m pytest -v
```

**Results:**
```
tests/test_agents.py ........                                            [ 27%]
tests/test_api.py ....                                                   [ 45%]
tests/test_data_analysis.py ......                                       [ 72%]
tests/test_paper_search.py ..                                            [ 81%]
tests/test_plugins.py ....                                               [100%]

======================= 22 passed in 27s =======================
```

---

## 📝 8. Demo Walkthrough

1. **Step 1: Input Idea**: Select or type *"Deep Learning for Real-Time Plant Disease Detection in Complex Field Environments"*. Choose the CSE domain plugin and click **Launch Autonomous Research Team**.
2. **Step 2: Literature Discovery**: Inspect surveyed arXiv & Semantic Scholar paper cards with methods, datasets, and limitations automatically extracted. Ask the RAG assistant questions about prior research.
3. **Step 3: Gap Analysis**: Review the comparison matrix showing existing baselines, observed field failure modes, and novel contribution opportunities.
4. **Step 4: Methodology Design**: View the step-by-step pipeline stages, recommended benchmark models, and validation protocols. Run the interactive sample size or IEEE standard calculator.
5. **Step 5: Data Lab**: Select the built-in sensor dataset or upload custom CSV. Inspect statistical distributions, correlation heatmaps, trained Random Forest baselines, and scientific interpretations.
6. **Step 6: Export**: View the formatted research proposal blueprint and download the `.md` or `.tex` manuscript.

---

## 🤝 9. Contributing & Hacktoberfest

Contributions from students, researchers, and open-source developers are enthusiastically welcomed!

- Read our [CONTRIBUTING.md](CONTRIBUTING.md) for full development setup and domain plugin tutorials.
- Create new domain plugins under `domains/` (e.g. `domains/agriculture`, `domains/medicine`, `domains/chemistry`).
- All valid, high-quality pull requests will be reviewed and tagged with `hacktoberfest-accepted`.

---

## 🗺️ 10. Future Roadmap

- [ ] Support for native ChromaDB persistent server embeddings.
- [ ] Integration with IEEE Xplore and PubMed APIs.
- [ ] Automated LaTeX bibliography (`references.bib`) generation.
- [ ] Multi-turn interactive agent dialogue allowing collaborative human-in-the-loop editing.
- [ ] Single-click export to Overleaf and Google Docs.

---

## 📄 License

Licensed under the **Apache License, Version 2.0**. See [LICENSE](LICENSE) for details.
