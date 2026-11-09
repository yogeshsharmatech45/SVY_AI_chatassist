# Sample website for GitHub Pages

A fast, single-page site for your WhatsApp AI receptionist service: hero with a scripted Hinglish booking conversation,
what it handles, go-live timeline, live demo chat (optional), pricing, FAQ, and WhatsApp/email contact buttons.
No build step. Plain HTML, CSS and a little JavaScript.

## 1. Edit your details (2 minutes)
Open `index.html`, find the block marked `EDIT THESE FOUR LINES` near the bottom, and change:

| Setting | Example |
|---|---|
| `brand` | your business name |
| `whatsappNumber` | `919812345678` (country code + number, digits only) |
| `email` | `you@yourdomain.in` |
| `chatWebhookUrl` | leave empty for now (see step 4) |

Also search for `ReplyMitra` in `index.html` and `privacy.html` and replace it with your final name (it is only a working name;
check it is free before you use it). Prices in the pricing section are placeholders from our plan; change them to yours.
Fill in the [bracketed] parts of `privacy.html`.

## 2. Publish on GitHub Pages (10 minutes)
1. Create a free account at github.com.
2. Click **New repository**. Name it `yourusername.github.io` (becomes your home page) or any name such as `chatbot-site`. Set it **Public**.
3. Upload all files from this folder (**Add file, Upload files**), or with git:
   ```bash
   git init -b main
   git add .
   git commit -m "Initial site"
   git remote add origin https://github.com/YOURUSERNAME/YOURREPO.git
   git push -u origin main
   ```
4. In the repo go to **Settings, Pages**. Under **Source** choose **Deploy from a branch**, branch `main`, folder `/ (root)`, then **Save**.
5. After a minute or two your site is at `https://YOURUSERNAME.github.io/` (or `/YOURREPO/` for a project repo).
6. Optional custom domain: in **Settings, Pages, Custom domain** enter your domain and add the DNS record GitHub shows you; tick **Enforce HTTPS**.

If you used a project repo (not `username.github.io`), change `href="/"` to `href="/YOURREPO/"` and `href="/favicon.svg"` to `href="/YOURREPO/favicon.svg"` in `404.html`.

## 3. Check it
Open the site on your phone and laptop. The WhatsApp buttons should open a chat with your number, and the conversation in the hero should play once and replay on demand.

## 4. Turn on the live demo chat (optional)
The demo box shows an "offline" card until you give it your n8n chat address.
1. In the demo project (`whatsapp-ai-demo`), open workflow **Demo 1 - Website chat (Claude)** in n8n and switch it to **Active**.
2. Your n8n must be reachable from the internet over https. For demos use a Cloudflare tunnel (`cloudflared tunnel --url http://localhost:5678`) and set `WEBHOOK_URL` in the demo's `.env` to the tunnel address, then `docker compose up -d n8n`.
3. Your production chat address is:
   `https://YOUR-TUNNEL-ADDRESS/webhook/24303116-045f-549c-8ff4-869e79609f94/chat`
   Paste it into `chatWebhookUrl` in `index.html`, then commit and push.
4. Quick tunnels change address each time you restart them, and your laptop must be on while visitors use the demo. For a permanent demo, host n8n on a small VPS with https.

The widget loads `@n8n/chat` version 1.44.3 from the jsDelivr CDN. If you bump the version, test the demo again.

## 5. Important notes
- **GitHub's rules:** GitHub says Pages is not allowed as free hosting to run an online business or a site mainly for commercial transactions. A sample or portfolio site is generally fine. For the real, client-facing business site, move the same files to **Cloudflare Pages** (upload the folder, no changes needed) or Netlify.
- **Honest claims:** The FAQ promises things (data deletion, a 48-hour demo, reminders in Growth, CRM sync in Pro). Only keep promises you will deliver. The demo project does not include reminders or CRM sync yet.
- **Privacy page:** it is a template, not legal advice. Fill it in properly and get it reviewed before you collect real customer data.
- **Fonts:** Google Fonts are loaded from Google. If you prefer no external requests, delete the font links and the site falls back to system fonts.
- **Trademarks:** keep the "WhatsApp is a trademark of Meta" line, and do not put "WhatsApp" in your business name or domain.

## Files
```
index.html      the whole site
privacy.html    privacy template
404.html        not-found page
favicon.svg     icon
robots.txt      search engine rules
.nojekyll       tells GitHub Pages to serve the files as they are
```
