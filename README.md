# Skener Faktúr / Invoice Scanner

AI-powered batch receipt and invoice scanner that extracts structured data and exports to Excel.

## Features

- **Multi-page PDF support** — sends entire PDFs to Claude, which reads all pages at once
- **Image support** — JPEG, PNG, GIF, WebP
- **Batch processing** — drop an entire folder of invoices
- **Slovak/Czech business fields** — IČO, DIČ, IČ DPH, IBAN
- **Excel export** with 4 sheets: Summary, Line Items, Vendors, Errors
- **Detail view** — click any row to see full extracted data
- **Runs entirely in your browser** — no server needed

## Setup

### 1. Get an Anthropic API key

Go to [console.anthropic.com/settings/keys](https://console.anthropic.com/settings/keys) and create a key.

### 2. Deploy to GitHub Pages

```bash
# Create a new repo
git init invoice-scanner
cd invoice-scanner

# Copy index.html into the repo
cp index.html .

# Push to GitHub
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/invoice-scanner.git
git push -u origin main
```

Then in your GitHub repo: **Settings → Pages → Source: Deploy from branch → Branch: main → Save**

Your app will be live at `https://YOUR_USERNAME.github.io/invoice-scanner/`

### 3. Use it

1. Open the page
2. Enter your Anthropic API key (stored only in your browser's localStorage)
3. Drop files or a folder
4. Click "Spracovať všetko" (Process all)
5. Download Excel when done

## How it works

Each file is sent to Claude Sonnet's vision API:
- **PDFs** → sent as `document` type (Claude reads all pages)
- **Images** → sent as `image` type

Claude extracts structured JSON with vendor info, line items, tax details, and business identifiers. The app then assembles everything into an Excel workbook.

## Privacy

- Your API key is stored only in your browser's localStorage
- Files are sent directly from your browser to the Anthropic API
- No data passes through any intermediary server

## License

MIT
