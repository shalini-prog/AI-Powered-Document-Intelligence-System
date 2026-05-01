📄 AI Document Processing & Automation System

An AI-powered document intelligence platform that automates:

📥 Document ingestion (Upload / Email)
🔍 OCR text extraction
🔐 PII masking
🧠 AI-based data extraction
📊 Smart decision making
🗂️ Department-wise storage

📌 Overview

This system processes documents using OCR + LLM + Automation pipelines to:

Identify document type
Extract structured data
Detect sensitive information
Automatically route documents

🚀 Key Features

📥 Multi-Source Document Input
Upload via API
Email attachment ingestion (IMAP)

🔍 OCR Processing
Supports:
Images (JPG, PNG)
PDFs
Uses Tesseract OCR

🔐 PII Masking
Detects and anonymizes:
Names
Emails
Phone numbers
Uses Microsoft Presidio

🧠 AI Document Understanding
Uses LLM (Groq - LLaMA 3.1)
Automatically extracts structured data

⚙️ Smart Decision Engine
AUTO_APPROVED
REVIEW_REQUIRED

🗂️ Intelligent Routing

Documents are stored in:

Finance (Invoices)
HR (Resumes)
Legal (Contracts)
General

⚡ Background Processing
Celery workers
Redis queue
Async document processing

📊 Dashboard APIs
View all documents
Fetch individual document

🏗️ System Architecture

User / Email Input
        ↓
FastAPI Backend
        ↓
Celery Queue (Redis)
        ↓
Worker Processing
   ├── OCR (Tesseract)
   ├── PII Masking (Presidio)
   ├── LLM Extraction (Groq)
   └── Decision Engine
        ↓
Supabase Database
        ↓
Dashboard APIs

⚙️ Tech Stack

Backend: FastAPI
Queue System: Celery + Redis
OCR: Tesseract
LLM: Groq (LLaMA 3.1)
PII Detection: Presidio
Database: Supabase
Email Integration: IMAP

📁 Project Structure

app/
│
├── routes/
│   ├── upload.py
│   ├── email.py
│   └── documents.py
│
├── services/
│   ├── email_service.py
│   ├── llm_service.py
│   ├── pii_service.py
│   └── supabase_service.py
│
├── workers/
│   ├── celery_app.py
│   ├── tasks.py
│   └── email_tasks.py
│
└── main.py

data/
└── uploads/

📡 API Endpoints

📥 Upload Document
POST /upload

📧 Fetch Email Attachments
POST /api/email/fetch

📄 Get All Documents
GET /api/documents

📄 Get Single Document
GET /api/document/{filename}

🧠 Processing Pipeline

Step 1: Upload / Email Fetch
Step 2: OCR Extraction
Step 3: PII Masking
Step 4: LLM Data Extraction
Step 5: Decision Engine
Step 6: Supabase Storage

⚙️ Setup Instructions

1️⃣ Clone Repository
git clone https://github.com/your-username/ai-document-system.git
cd ai-document-system

2️⃣ Install Dependencies
pip install -r requirements.txt

3️⃣ Setup Environment Variables

Create .env:

GROQ_API_KEY=your_groq_key
SUPABASE_URL=your_url
SUPABASE_KEY=your_key
EMAIL_USER=your_email
EMAIL_PASS=your_password

4️⃣ Install External Tools
🔹 Tesseract OCR
Install and set path:
pytesseract.pytesseract.tesseract_cmd = "YOUR_PATH"
🔹 Poppler (for PDFs)
Required for PDF processing

5️⃣ Start Redis
redis-server

6️⃣ Run Celery Worker
celery -A app.workers.celery_app worker --loglevel=info

7️⃣ Run Celery Beat (Scheduler)
celery -A app.workers.celery_app beat --loglevel=info

8️⃣ Run FastAPI Server
uvicorn app.main:app --reload

📊 Example Output
{
  "document_type": "invoice",
  "extracted_data": {
    "invoice_number": "12345",
    "total_amount": "₹10,000",
    "vendor": "ABC Pvt Ltd"
  },
  "decision": "AUTO_APPROVED"
}

🔐 Security Features

PII masking before AI processing
Safe JSON parsing
Input size limiting
Error handling & fallback

📈 Future Enhancements

📊 Web dashboard (React UI)
🔍 Document search & filtering
🧾 Multi-language OCR
🤖 Fine-tuned LLM
☁️ Cloud deployment
👨‍💻 Author

Developed as part of an AI Automation & Document Intelligence System

📜 License

MIT License

⭐ Support

If you like this project:

⭐ Star the repo
🍴 Fork it
🚀 Contribute
