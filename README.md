# python-s3finder
Automated Python tool to detect real AWS S3 buckets with exact region detection.
# Python S3Finder

**Python S3Finder** — precise AWS S3 detection for a target domain.  
Scans enumerated subdomains, filters live hosts, probes standard S3 endpoints and extracts exact S3 bucket regions using `x-amz-bucket-region`. Produces a compact JSON report and evidence snippets.

## Features
- Subdomain enumeration (Subfinder & Sublist3r)
- Live host filtering using `httpx` (fallback to all subdomains if `httpx` not available)
- Precise S3 detection (reads `x-amz-bucket-region` header)
- Low false-positive rate (ignores generic 200 OK pages)
- Multi-threaded scanning (`--workers`)
- JSON report output

## Prerequisites
- Python 3.8+ and `pip`.  
- `requests` Python library:
  ```bash
  pip install requests

sub

(Optional but recommended) 
subfinder — passive subdomain enumeration (ProjectDiscovery).
https://github.com/projectdiscovery/subfinder.git

(Optional) Sublist3r — OSINT-based subdomain enumeration (Python). GitHub: Sublist3r. 
https://github.com/aboul3la/Sublist3r.git

(Optional) httpx — fast HTTP probing tool (ProjectDiscovery). Used to filter live hosts. 
GitHub
https://github.com/projectdiscovery/httpx.git

If httpx is not available the script falls back to scanning all enumerated subdomains.

Usage
python3 s3finder.py -d example.com --subfinder --sublist3r -w 20
