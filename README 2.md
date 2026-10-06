# IMO LIFE — Online Google Login Build

This build is prepared for public deployment with Google sign-in. It uses React/Vite, Framer Motion and Supabase Auth. Game state is currently saved per Google account in browser localStorage; the included `supabase.sql` is a starting point for moving player state to Supabase cloud storage.

## 1. Create Supabase
Create a project at https://supabase.com/dashboard.

In Authentication → Providers, enable Google. Google OAuth requires a Google Cloud OAuth client and your deployed URL/redirect configuration.

Copy your Project URL and publishable key into `.env.local`:

```
VITE_SUPABASE_URL=https://YOUR_PROJECT.supabase.co
VITE_SUPABASE_PUBLISHABLE_KEY=YOUR_PUBLISHABLE_KEY
```

## 2. Run locally
```
npm install
npm run dev
```

## 3. Deploy
Push this folder to GitHub, then import the repo into Vercel. Add the two `VITE_` environment variables in Vercel. Vercel will provide a public `.vercel.app` URL.

## 4. Google redirect
In Google Cloud OAuth credentials, add the deployed site as an authorized JavaScript origin. In Supabase Auth URL Configuration, set the Site URL and redirect URL to the deployed address.

## 5. Cloud persistence
Run `supabase.sql` in the Supabase SQL editor and then wire game writes to `public.players` if you want player data to follow the account across browsers/devices. Messages can similarly be moved into a table with RLS.
