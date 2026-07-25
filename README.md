# Heritage Explorer - Cultural Tourism Platform

A comprehensive web application for discovering and exploring cultural heritage destinations, stories, events, and virtual tours.

## Features

- 🏛️ **Destinations** - Browse cultural heritage sites with detailed information, images, and maps
- 📖 **Stories** - Read and submit cultural stories from around the world
- 🎉 **Events** - Discover upcoming cultural events and festivals
- 🎯 **Experiences** - Find guided tours, workshops, and cultural activities
- 🎥 **Virtual Tours** - Explore heritage sites through immersive virtual experiences
- 🗺️ **Interactive Maps** - View destinations on Mapbox-powered maps
- 🔐 **Admin Dashboard** - Manage all content with role-based access control
- 🔖 **Bookmarks** - Save your favorite destinations
- 📱 **Responsive Design** - Works seamlessly on desktop and mobile

## Tech Stack

- **Frontend**: React 18, TypeScript, Vite
- **Styling**: Tailwind CSS, shadcn/ui components
- **Backend**: Supabase (Database, Auth, Storage, Edge Functions)
- **Maps**: Mapbox GL JS
- **State Management**: TanStack Query (React Query)
- **Routing**: React Router DOM
- **Forms**: React Hook Form with Zod validation

## Prerequisites

- Node.js 18+ and npm
- A Supabase project (or use Lovable Cloud)
- Mapbox access token (for maps functionality)

## Getting Started

### 4. Database Setup

If setting up manually, run the migrations in `supabase/migrations/` to create:

- `destinations` - Heritage sites and locations
- `stories` - Cultural stories and articles
- `events` - Cultural events and festivals
- `experiences` - Tours and activities
- `virtual_tours` - Virtual tour content
- `profiles` - User profiles
- `bookmarks` - User saved destinations
- `user_roles` - Role-based access control

### 5. Configure Secrets

For the application to work properly, configure the following credentials either via **Admin Panel → Settings** or as Cloud secrets, and use `.env.example` to create your local `.env` file.

#### Required environment variables

- `VITE_SUPABASE_URL`
- `VITE_SUPABASE_PUBLISHABLE_KEY`
- `VITE_MAPBOX_TOKEN`
- `OPENAI_API_KEY`
- `SUPABASE_SERVICE_ROLE_KEY`

You can create a local file from the example:

```bash
cp .env.example .env
```

Then update the values for your Supabase, Mapbox, and OpenAI access keys.

---

## 🤖 AI Chatbot Setup

The AI chatbot is powered by a Supabase Edge Function and OpenAI. Configure `OPENAI_API_KEY` in your function environment for the chatbot to work.

The new chatbot page is available at `/chatbot`.

---

## 📧 Gmail SMTP Setup Guide

The contact form uses Gmail SMTP to send emails. Follow these steps to set it up:

### Step 1: Enable 2-Step Verification
1. Go to [Google Account Security](https://myaccount.google.com/security)
2. Enable **2-Step Verification** if not already enabled

### Step 2: Generate App Password
1. Visit [App Passwords](https://myaccount.google.com/apppasswords) in your Google Account
2. Select **Mail** as the app
3. Select **Other (Custom name)** as the device
4. Enter a name like "Heritage Site" or your project name
5. Click **Generate**

### Step 3: Copy the Password
- Google will display a 16-character password
- Copy this password (spaces are optional)
- **Important**: This is the only time you'll see this password

### Step 4: Configure in Admin Panel
Go to **Admin → Settings → Email Configuration** and enter:
- **Gmail User**: Your full Gmail address (e.g., `yourname@gmail.com`)
- **Gmail App Password**: The 16-character password from Step 3
- **Contact Email**: Email where you want to receive form submissions

> ⚠️ **Security Note**: Never use your regular Gmail password. App Passwords are designed for third-party apps and can be revoked anytime without affecting your main account.

---

## 🗺️ Mapbox Setup Guide

Interactive maps require a Mapbox access token. Follow these steps:

### Step 1: Create Mapbox Account
1. Go to [Mapbox Sign Up](https://account.mapbox.com/auth/signup/)
2. Create a free account (no credit card required)

### Step 2: Get Access Token
1. Visit [Access Tokens](https://account.mapbox.com/access-tokens/) page
2. You can use the **Default public token** or create a new one

### Step 3: Configure in Admin Panel
Go to **Admin → Settings → Map Configuration** and enter:
- **Mapbox Public Token**: Your token (starts with `pk.`)

> 💡 **Free Tier**: Mapbox offers 50,000 free map loads per month, sufficient for most small to medium websites.

---

### 6. Run Development Server

// npm install

```bash
npm run dev
```

The app will be available at `http://localhost:5173`

## Project Structure

```
src/
├── components/
│   ├── admin/          # Admin dashboard components
│   ├── cards/          # Reusable card components
│   ├── destination/    # Destination detail components
│   ├── home/           # Homepage sections
│   ├── layout/         # Navbar, Footer
│   ├── search/         # Search functionality
│   ├── stories/        # Story components
│   └── ui/             # shadcn/ui components
├── contexts/           # React contexts (Auth)
├── hooks/              # Custom React hooks
├── pages/              # Route pages
├── types/              # TypeScript types
└── lib/                # Utility functions

supabase/
├── functions/          # Edge functions
│   ├── get-mapbox-token/
│   ├── search-places/
│   └── send-contact-email/
└── migrations/         # Database migrations
```

## Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build
- `npm run lint` - Run ESLint

## User Roles

- **User** - Browse content, bookmark destinations, submit stories
- **Editor** - All user permissions + manage content
- **Admin** - Full access including user management

## Deployment


### Manual Deployment

1. Build the project: `npm run build`
2. Deploy the `dist/` folder to your hosting provider
3. Configure environment variables on your host

