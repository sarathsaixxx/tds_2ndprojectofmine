# FastAPI Project Setup with Virtual Environment and GEMAI_API_KEY

This guide walks you through setting up a Python virtual environment, installing dependencies, and running a FastAPI application using `uvicorn`, while securely passing the `GEMAI_API_KEY` from your terminal.

---

## Prerequisites

- Python 3.8 or higher installed
- `pip` installed (comes with Python)
- Access to [Google Cloud Console](https://console.cloud.google.com/) to create and manage API keys

---

## Step 1: Create and Activate a Virtual Environment

### Windows (CMD or PowerShell)

```bash
python -m venv venv
venv\Scripts\activate
```

### macOS / Linux

```bash
python3 -m venv venv
source venv/bin/activate
```

---

## Step 2: Install Dependencies

Ensure you have a `requirements.txt` file in your project directory.

```bash
pip install -r requirements.txt
```

---

## Step 3: Get Your GEMAI_API_KEY from Google Cloud

1. Go to [Google Cloud Console](https://console.cloud.google.com/).
2. Create a new project (or use an existing one).
3. Navigate to **APIs & Services > Credentials**.
4. Click **Create Credentials > API key**.
5. Copy the generated API key.
6. (Optional but recommended) Restrict the key to specific services and IPs.

---

## Step 4: Run the FastAPI App with Uvicorn

Assuming your FastAPI app is in a file named `main.py` and the app instance is named `app`:

### Run with API Key Passed as an Environment Variable

#### Windows (CMD)

```cmd
set GEMAI_API_KEY=your_api_key_here
uvicorn main:app --reload
```

#### PowerShell

```powershell
$env:GEMAI_API_KEY="your_api_key_here"
uvicorn main:app --reload
```

#### macOS / Linux

```bash
export GEMAI_API_KEY=your_api_key_here
uvicorn main:app --reload
```

---

## Step 5: Access the App

Open your browser and navigate to:

```
http://127.0.0.1:8000
```

To test and interact with your API via Swagger UI, visit:

```
http://127.0.0.1:8000/docs
```

---

## (Optional) Use `.env` File with `python-dotenv`

If you want to avoid setting the API key every time, you can:

1. Install `python-dotenv` (add to `requirements.txt`):

   ```bash
   pip install python-dotenv
   ```

2. Create a `.env` file:

   ```env
   GEMAI_API_KEY=your_api_key_here
   ```

3. Load it in your app (`main.py`):

   ```python
   from dotenv import load_dotenv
   import os

   load_dotenv()

   gemai_api_key = os.getenv("GEMAI_API_KEY")
   ```

---

## Done!

```

---

Let me know if you also want a sample `requirements.txt` or `main.py` template for this setup.
```
