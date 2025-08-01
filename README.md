# Question Answering Using RAG (Retrieval-Augmented Generation)
This repository demonstrates <b>Retrieval-Augmented Generation (RAG)</b> for question answering using LangChain, Hugging Face Transformers, and FAISS given a document as input.

The pipeline retrieves relevant documents from a vector database and uses a QA model to generate accurate, context-aware answers. Accompanying these context-aware answers is also a brief excerpt of the passage from the document that answers the question, further strengthening the validity of the answer. In cases of irrelevant answers, it correctly identifies the out-of-context question and gives an appropriate response.

## Features
* RAG pipeline with LangChain and FAISS vector store
* Contextual question answering using Hugging Face Transformers
* Sentence embeddings powered by sentence-transformers
* Customizable retrieval parameters (top_k, chunk size, etc.)
* Ready-to-run on Google Colab (recommended) or local environments

## How It Works
### 1. Document Loading
Loads PDF file.
Splits documents into manageable chunks for embeddings.
### 2. Embedding and Vector Store Creation
Uses sentence-transformers to create embeddings.
Stores embeddings in FAISS for efficient retrieval.
### 3. Question Answering
Retrieves the top k most relevant documents.
Feeds the retrieved context and user query into a Hugging Face QA pipeline.
Returns an answer with relevant supporting context unadultered from the document.

## Usage
### Question
```
response = answer_with_context(
    question="What is Machine Learning?",
    top_k=3
)

print("Answer:", response["answer"])
print("Context:", response["context"])
```
### Example output
```
Answer: a field of science
Relevant Context:
- Machine learning is a field of science that utilizes data and algorithms to train computers.
```
