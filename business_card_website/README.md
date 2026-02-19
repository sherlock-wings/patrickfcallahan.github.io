# Patrick F. Callahan - Personal Website

Personal portfolio website built with vanilla HTML, CSS, and JavaScript. Hosted on GitHub Pages.

## Structure

```
├── index.html              # Main single-page site
├── assets/
│   ├── css/style.css       # Styles
│   └── js/main.js          # JavaScript
├── CNAME                   # Custom domain config
└── bluesky-analytics/      # Streamlit app (separate repo)
```

## Deployment

### GitHub Pages (Main Site)

1. **Create GitHub repository:**
   ```bash
   # Initialize git in this directory
   git init
   git add .
   git commit -m "Initial commit"
   
   # Create repo on GitHub named: patrickfcallahan.github.io
   # Then push:
   git remote add origin https://github.com/patrickfcallahan/patrickfcallahan.github.io.git
   git branch -M main
   git push -u origin main
   ```

2. **Enable GitHub Pages:**
   - Go to repo Settings → Pages
   - Source: Deploy from a branch
   - Branch: `main` / `/ (root)`
   - Save

3. **Configure custom domain:**
   - In repo Settings → Pages → Custom domain
   - Enter: `patrick-f-callahan.com`
   - Check "Enforce HTTPS"

4. **DNS (already done in Cloudflare):**
   - A records pointing to GitHub's IPs
   - CNAME for `www` pointing to `patrickfcallahan.github.io`

Your site will be live at `https://patrick-f-callahan.com` within minutes.

### Streamlit App (Bluesky Analytics)

The `bluesky-analytics/` folder should be deployed as a **separate repository**:

1. **Create separate repo:**
   ```bash
   cd bluesky-analytics
   git init
   git add .
   git commit -m "Initial commit"
   
   # Create repo on GitHub named: bluesky-analytics
   git remote add origin https://github.com/patrickfcallahan/bluesky-analytics.git
   git branch -M main
   git push -u origin main
   ```

2. **Deploy to Streamlit Cloud:**
   - Go to [share.streamlit.io](https://share.streamlit.io)
   - Sign in with GitHub
   - Click "New app"
   - Select your `bluesky-analytics` repo
   - Main file: `app.py`
   - Click "Deploy"

3. **Add Snowflake secrets:**
   - In Streamlit Cloud, go to your app
   - Click "Settings" (⚙️) → "Secrets"
   - Add your Snowflake credentials:
   ```toml
   [snowflake]
   user = "your_username"
   password = "your_password"
   account = "your_account.region"
   warehouse = "your_warehouse"
   database = "your_database"
   schema = "your_schema"
   ```

4. **Update main site link:**
   - Once deployed, update the Streamlit URL in `index.html`
   - Default will be: `https://bluesky-analytics.streamlit.app`

## Local Development

### Main Site
Simply open `index.html` in a browser, or use a local server:
```bash
# Python
python -m http.server 8000

# Node.js
npx serve .
```

### Streamlit App
```bash
cd bluesky-analytics
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
cp .streamlit/secrets.toml.example .streamlit/secrets.toml
# Edit secrets.toml with your credentials
streamlit run app.py
```

## Customization

### Update Personal Info
Edit `index.html` to update:
- Name and title
- About section
- Experience/timeline
- Skills
- Project descriptions
- Contact links (email, GitHub, LinkedIn)

### Styling
Modify `assets/css/style.css`:
- Colors: Update CSS variables in `:root`
- Fonts: Change Google Fonts import and `--font-sans`
- Layout: Adjust spacing and breakpoints

## License

MIT
