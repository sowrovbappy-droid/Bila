# AI Web App

A responsive AI chat starter built with Express, SQLite (via sql.js), vanilla HTML/CSS/JS, sessions, and a configurable OpenAI-compatible chat-completions endpoint.

## Requirements
- Node.js 20+ and npm
- An AI provider API endpoint, API key, and model for real AI replies
- Acode is the editor; Termux runs Node.js and the backend.

## Run in Termux
```bash
pkg update
pkg install nodejs git
mkdir -p ~/ai-web-app
# Extract this ZIP into ~/ai-web-app, then:
cd ~/ai-web-app
npm install
cp .env.example .env
```
Edit `.env` and set a long random `SESSION_SECRET`. Add `AI_API_KEY`, `AI_MODEL`, and the provider endpoint if you want real AI responses. Never share the `.env` file or commit it.

Start:
```bash
npm start
```
Open `http://127.0.0.1:3000` in the browser on the same phone.

To test on another device on the same trusted Wi-Fi, find the phone's LAN IP and open `http://PHONE_LAN_IP:3000`; only do this on a trusted network. Do not expose the development server directly to the public internet.

## Admin
Set `ADMIN_EMAIL` to the email address of the account you want to administer, then register using that same email. Admin role is derived server-side from this setting. Do not use a public or shared email for this purpose.

## Database
The app stores SQLite data in `data/app.sqlite` using sql.js and writes changes to disk. Back up this file while the app is stopped. For high-traffic production use, prefer a server-hosted database and a durable session store.

## Security and production notes
- API keys remain on the server.
- Configure a strong `SESSION_SECRET`; use HTTPS and secure cookies in production.
- This starter uses the default in-memory session store, which is not suitable for production. Configure a durable session store before deployment.
- AI providers may charge for API usage. Set provider quotas and monitor usage.
- `AI_API_URL` must be a compatible chat-completions endpoint; not every provider uses the same format.
- Before public deployment, review CORS, session storage, account recovery, privacy policy, abuse controls, backups, monitoring, and applicable laws.

## Features
- Responsive chat interface, dark/light theme
- Registration, login, logout
- Saved conversations and messages
- Conversation rename/delete
- Server-side AI API call
- Admin statistics view
- Basic rate limits, Helmet, input validation, ownership checks
- Automated smoke tests

This is a working starter, not a claim of production certification. Test and harden it before handling real users or sensitive information.
