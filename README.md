# Local RAG Pizza Restaurant Assistant 🍕🤖

An interactive, Retrieval-Augmented Generation (RAG) command-line application built with Python. This project uses local Large Language Models (LLMs) to answer questions about a pizza restaurant by retrieving context from a vector database of customer reviews.

Everything runs 100% locally using **LangChain**, **ChromaDB**, and **Ollama**, ensuring complete data privacy and zero API costs.

## 🚀 Features
* **Local LLM Execution:** Powered by Ollama using the `llama3.2` model.
* **Vector Search Engine:** Stores and retrieves reviews using **ChromaDB**.
* **Semantic Embeddings:** Uses `mxbai-embed-large` to map text into high-dimensional space for accurate context retrieval.
* **Interactive CLI:** A continuous chat loop to query the restaurant's reviews in real-time.

## 🛠️ Prerequisites

Before running this project, ensure you have the following installed:
1. **Python 3.8+**
2. **[Ollama](https://ollama.com/)** (Running locally on your machine)

## 📦 Installation & Setup

**1. Clone the repository**
```bash
git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
cd your-repo-name
```

**2. Install Python dependencies**
Create a virtual environment (optional but recommended) and install the required LangChain and data processing libraries:
```bash
pip install langchain-ollama langchain-chroma langchain-core pandas
```

**3. Pull the required Ollama Models**
Make sure the Ollama application is running, then open your terminal and download the specific models used in this project:
```bash
# Pull the LLM for text generation
ollama pull llama3.2

# Pull the embedding model for vectorizing reviews
ollama pull mxbai-embed-large
```

**4. Prepare your data**
Ensure you have the CSV file named `realistic_restaurant_reviews.csv` in the root directory. It should contain at least the following columns: `Title`, `Review`, `Rating`, and `Date`.

## 💻 Project Structure

* `vector.py`: Handles data ingestion. It reads the CSV file, generates embeddings for each review, and stores them in a local Chroma vector database (`./chrome_langchain_db`).
* `main.py`: The main application script. It initializes the `llama3.2` model, sets up the prompt template, connects to the Chroma retriever, and runs the interactive chat loop.

## 🏃‍♂️ How to Run

Run the main application script:

```bash
python main.py
```

**What happens next?**
1. **First Run:** If the Chroma database doesn't exist, `vector.py` will automatically parse your CSV, generate embeddings, and create the database in your project folder. *(Note: This might take a moment depending on your hardware).*
2. **Subsequent Runs:** It will skip the embedding process and immediately load the existing vector store, making startup lightning fast.
3. **Chat Loop:** The CLI will prompt you to ask a question. Try asking things like:
   * *"What do people say about the pepperoni pizza?"*
   * *"Are there any complaints about the service?"*
   * *"Is the restaurant family-friendly based on reviews?"*

Type `q` to quit the application.

## 🧠 Technologies Used
* **LangChain:** Framework for developing LLM applications.
* **ChromaDB:** Open-source vector database.
* **Ollama:** Framework for running LLMs locally.
* **Pandas:** Data manipulation and analysis.
