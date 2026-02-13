# Valentine site

Two-page site: ask “Will you be my Valentine?” then show a thank-you page.

## Setup

1. Add your images to this folder:
   - **couple.jpeg** – photo of you two (main page)
   - **celebration.jpeg** – celebratory image (thank-you page)

2. Host on your laptop with one of these:

   **Option A – Python (if you have Python installed)**  
   In Terminal, from this folder run:
   ```bash
   cd /Users/rishabhdalal/Desktop/valentine-site
   python3 -m http.server 8000
   ```
   Then open: **http://localhost:8000**  
   If you see "Address already in use", try another port: `python3 -m http.server 5500` and open **http://localhost:5500** (or 8080, 8888, 9000).

   **Option B – Node (if you have Node/npm)**  
   ```bash
   npx serve .
   ```
   Then open the URL shown (e.g. http://localhost:3000).

3. On your phone: use the same Wi‑Fi as your laptop, find your laptop’s IP (e.g. System Settings → Network), then on the phone open `http://YOUR_IP:8000` (or the port from Option B).

---

## Hosting on your domain (e.g. ilu.com)

You need to do two things: **put the site on a server** and **point your domain to that server**.

### Step 1: Deploy the site to a host

Your site is static (HTML/CSS/JS and images), so free static hosting works well.

| Option | Best if you… | What you do |
|--------|----------------|-------------|
| **Netlify** | Want the simplest setup | Drag the project folder to [app.netlify.com/drop](https://app.netlify.com/drop), or connect a Git repo. You get a URL like `something.netlify.app`. |
| **Vercel** | Like Netlify or use Node | Sign up at [vercel.com](https://vercel.com), import the project (or drag folder). You get a URL like `something.vercel.app`. |
| **GitHub Pages** | Use GitHub | Push this folder to a repo, enable Pages in repo Settings → Pages, choose “Deploy from branch”. You get `username.github.io/repo-name`. |

**What to upload:** the whole project folder, including `index.html`, `thankyou.html`, `couple.jpeg`, `celebration.jpeg`, and any other files. No need to upload `README.md` unless you want.

After Step 1 you should be able to open the site at the URL the host gives you (e.g. `https://your-site.netlify.app`). Check that both pages and images work.

### Step 2: Point ilu.com to your host

Where you do this depends on **where you bought ilu.com** (GoDaddy, Namecheap, Google Domains, Cloudflare, etc.). Log in there and open **DNS settings** for `ilu.com`.

**If you use Netlify or Vercel:**  
They’ll ask you to add a **custom domain** (e.g. `ilu.com` and optionally `www.ilu.com`). In your domain registrar’s DNS you’ll add what they tell you, usually:

- **A record:** `@` (or leave “name” blank) → point to the IP they give you, **or**
- **CNAME record:** `www` → `your-site.netlify.app` (or the host’s URL they show you)

**If you use GitHub Pages:**  
In the repo: Settings → Pages → Custom domain → set `ilu.com`. Then in your domain’s DNS add the A/CNAME records GitHub shows you.

**At your domain registrar you typically add:**

- For **root domain** `ilu.com`: an **A record** with the host’s IP, or a CNAME/ALIAS/ANAME if your registrar supports it (Netlify/Vercel explain this).
- For **www.ilu.com**: a **CNAME** record: `www` → your host’s URL (e.g. `your-site.netlify.app`).

DNS can take from a few minutes up to 24–48 hours to update. After it propagates, `ilu.com` (and `www.ilu.com` if you set it) will open your Valentine site. The host will usually provide **HTTPS** automatically.

### Quick checklist

1. [ ] Deploy the folder to Netlify, Vercel, or GitHub Pages.  
2. [ ] Add custom domain `ilu.com` (and `www.ilu.com` if you want) in the host’s dashboard.  
3. [ ] In your domain registrar’s DNS, add the A and/or CNAME records the host tells you.  
4. [ ] Wait for DNS to propagate, then visit **https://ilu.com**.
