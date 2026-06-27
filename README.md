# YouTube RAG Chatbot

A Retrieval Augmented Generation (RAG) chatbot that answers questions based on YouTube video transcripts using LangChain, Groq LLM, and FAISS vector search.

## 📋 Table of Contents

- [Features](#features)
- [Prerequisites](#prerequisites)
- [Setup and Installation](#setup-and-installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Project Architecture](#project-architecture)
- [Technologies Used](#technologies-used)

---

## ✨ Features

- 🎥 **YouTube Integration**: Automatically fetches video transcripts from any YouTube video
- 📝 **Smart Chunking**: Splits transcripts into manageable chunks for efficient processing
- 🔍 **Vector Search**: Uses FAISS for fast similarity search across embeddings
- 🤖 **AI-Powered Responses**: Leverages ChatGroq LLM to generate context-aware answers
- 🎨 **Interactive UI**: User-friendly ipywidgets interface for easy Q&A interaction
- ⚡ **Fast Retrieval**: Optimized embedding and retrieval pipeline for low-latency responses

---

## 📦 Prerequisites

- Google Colab environment (or local Python 3.8+)
- Groq API key ([Get one here](https://console.groq.com))
- Internet connection for YouTube transcript fetching

---

## 🚀 Setup and Installation

### 1. Install Dependencies

Run the following command in your notebook:

```bash
!pip install -q \
  langchain \
  langchain-community \
  langchain-groq \
  youtube-transcript-api \
  faiss-cpu \
  sentence-transformers \
  langchain-text-splitters
```

### 2. Configure API Key

The project uses the **Groq API** for the Large Language Model.

**Steps:**
1. Go to the **🔑 Secrets** icon in the left panel of Google Colab
2. Click on **"Secrets"**
3. Add a new secret named `GROQ_API_KEY`
4. Paste your Groq API key as the value
5. The notebook will automatically load and set it as an environment variable

### 3. Run the Notebook Sequentially

Execute notebook cells in order:

```
1. Install dependencies
2. Load the GROQ_API_KEY
3. Define your YouTube video_id
4. Fetch and process the transcript
5. Create embeddings and build FAISS vector store
6. Set up RAG pipeline
7. Run sample query
8. Launch interactive UI
```

---

## 💬 Usage

### Interactive UI

1. Scroll to the last code cell in the notebook
2. Run it to launch the interactive interface
3. You'll see the following input fields:

| Field | Description |
|-------|-------------|
| **Video ID** | YouTube video ID (e.g., `FwOTs4UxQS4`) |
| **Question** | Your question about the video content |
| **Get Answer** | Button to submit and receive response |

### Example

```
Video ID: FwOTs4UxQS4
Question: What are the main topics discussed in this video?
↓
[RAG Chatbot processes transcript and returns context-aware answer]
```

---

## 🏗️ Project Architecture

### Pipeline Components

```
YouTube Video
    ↓
[YouTubeTranscriptApi] → Fetch Transcript
    ↓
[RecursiveCharacterTextSplitter] → Chunk Text
    ↓
[HuggingFaceEmbeddings] → Create Embeddings
    ↓
[FAISS] → Store & Index Vectors
    ↓
[Retriever] → Find Relevant Context
    ↓
[PromptTemplate] → Structure Query
    ↓
[ChatGroq LLM] → Generate Response
```

### Key Modules

| Module | Purpose |
|--------|---------|
| **Data Ingestion** | Fetch YouTube transcripts and prepare data |
| **Text Processing** | Split transcripts into optimal chunks |
| **Vector Storage** | FAISS-based embedding storage and retrieval |
| **RAG Pipeline** | Combine retrieval with LLM generation |
| **User Interface** | ipywidgets for interactive Q&A |

---

## 🛠️ Technologies Used

| Technology | Purpose |
|-----------|---------|
| **LangChain** | LLM orchestration and RAG pipeline |
| **Groq API** | Fast LLM inference |
| **FAISS** | Vector similarity search |
| **HuggingFace** | Sentence embeddings |
| **YouTubeTranscriptApi** | Transcript extraction |
| **ipywidgets** | Interactive UI components |

---

## 📝 Notes

- Ensure your Groq API key has sufficient quota for your queries
- FAISS uses CPU by default (for GPU support, use `faiss-gpu`)
- Transcripts are cached during the session for faster subsequent queries
- Works best with videos that have auto-generated or manually added transcripts

---

## 📄 License

This project is open source and available under the MIT License.

---

## 🤝 Contributing

Contributions are welcome! Feel free to submit issues and pull requests.
