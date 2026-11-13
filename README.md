# Praveen Server Lab

A small, deployable Node.js + Express server diagnostics dashboard.

## Included
- Live CPU/load, memory, process uptime and host runtime metrics for the machine running the app
- DNS lookup (A, AAAA, MX, NS, TXT)
- TLS certificate inspection (issuer, validity and days remaining)
- Single-request website reachability check
- Public IP lookup from the browser
- Production security checklist

## Important safety design
This app does not include DDoS, traffic flooding, port scanning, exploit attempts, or server-crashing features.
Remote website checks are restricted to hostnames listed in `ALLOWED_TARGETS`. Add only domains you own or have explicit written permission to monitor. Requests use a single GET, have an 8-second timeout, and do not follow redirects.

## Run locally
Requires Node.js 20 or newer.

```bash
npm install
# Add your own authorized domain(s), comma-separated:
# Linux/macOS:
export ALLOWED_TARGETS="example.com,api.example.com"
# Windows PowerShell:
# $env:ALLOWED_TARGETS="example.com,api.example.com"
npm start
```

Open http://localhost:3000

## Deploy
Deploy this folder to a Node.js hosting provider that supports Node 20+.
- Build command: `npm install`
- Start command: `npm start`
- Environment variable: `ALLOWED_TARGETS=yourdomain.com,api.yourdomain.com`

Use HTTPS at your hosting provider. Do not put secrets in the browser code.
The dashboard's system metrics describe the hosting machine, not a third-party server.
