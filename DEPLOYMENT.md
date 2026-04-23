# DEPLOYMENT GUIDE: GROE AI

## 1. Prepare Project for Deployment

1. **GitHub Upload**:
   - Create a repository on GitHub (e.g., `groe-ai`).
   - Push your code to the `main` branch.
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/yourusername/groe-ai.git
   git push -u origin main
   ```

## 2. Deploy Frontend to Vercel or Netlify

### Option A: Vercel (Recommended)
1. Go to [Vercel](https://vercel.com/) and sign in.
2. Click **Add New** > **Project**.
3. Import your `groe-ai` repository from GitHub.
4. **Framework Preset**: Vercel will automatically detect Vite.
5. **Build Command**: `npm run build`
6. **Output Directory**: `dist`
7. Click **Deploy**.

### Option B: Netlify
1. Go to [Netlify](https://netlify.com/) and sign in.
2. Click **Add new site** > **Import an existing project**.
3. Connect your GitHub account and select the repository.
4. **Build Command**: `npm run build`
5. **Publish Directory**: `dist`
6. Click **Deploy Site**.

## 3. Deploy Backend to Render or Railway

### Backend Structure
The `backend/` folder contains a Node.js Express server.
1. Go to [Render](https://render.com/).
2. Click **New** > **Web Service**.
3. Connect your GitHub and select the repository.
4. Set the **Root Directory** to `backend`.
5. **Environment**: Node
6. **Build Command**: `npm install`
7. **Start Command**: `node server.js`
8. Add necessary Environment Variables (e.g., `PORT`, `JWT_SECRET`, `DATABASE_URL`).
9. Click **Create Web Service**.

## 4. Custom Domain Configuration (https://groeai.com)

1. Buy the domain `groeai.com` from a registrar (e.g., Namecheap, GoDaddy, Cloudflare).
2. Go to your Vercel/Netlify dashboard.
3. Navigate to **Settings** > **Domains**.
4. Add `groeai.com` and `www.groeai.com`.
5. Your hosting provider will give you DNS records to add:
   - **Type A Record**: Name `@`, Value (IP provided by Vercel/Netlify).
   - **CNAME Record**: Name `www`, Value `cname.vercel-dns.com` (or Netlify equivalent).
6. Go to your domain registrar's DNS settings and add these records.
7. Vercel/Netlify will automatically provision an SSL certificate, enabling HTTPS.

## 5. Security & Performance Verification

- HTTPS is enforced automatically via Vercel/Netlify.
- Frontend uses React and Vite for fast loading and optimized bundles.
- Backend (when connected) should use Helmet.js and CORS for basic protection.
