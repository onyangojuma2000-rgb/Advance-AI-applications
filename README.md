# PDF Question Answering Assistant

## What I built
A Python command-line tool that lets a user ask questions about a PDF. It:
- extracts selectable text from each PDF page;
- splits long documents into overlapping passages;
- selects passages that best match the question;
- sends those passages to Anthropic Claude;
- answers using the PDF content and reports page numbers where possible.

The tool is designed to reduce unsupported answers. If the information is not in the selected PDF extracts, it instructs Claude to say it could not find the answer.

**Note:** Scanned/image-only PDFs need OCR before this tool can read them. An Anthropic API key and internet connection are required for answers. Never share your API key publicly.

## Project files
- `pdf_qa.py` — main application
- `.env.example` — example environment-variable file
- `requirements.txt` — Python packages

## Setup in Windows PowerShell

Open this project folder in VS Code, then run:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
```

Create your own `.env` file by copying `.env.example`:

```powershell
Copy-Item .env.example .env
```

Open `.env` and add your Anthropic API key locally. Do not paste the key into chat or commit `.env` to GitHub.

## Run the assistant

Put a PDF anywhere you can point to, then run:

```powershell
python pdf_qa.py "C:\path\to\your-document.pdf"
```

Or run without a path and enter the PDF path when prompted:

```powershell
python pdf_qa.py
```

Ask questions in the terminal. Type `exit` to close the assistant.

## Example questions
- What is the total contract value?
- What are the payment terms?
- When is the delivery date?
- What penalty applies for late delivery?

## Important
The simple keyword retrieval works best when questions use terms that appear in the PDF. It is not OCR software, and it does not guarantee perfect answers. Verify important legal, financial, or contractual details against the original document.
