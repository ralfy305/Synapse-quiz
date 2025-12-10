# RelateAI - Mediated Communication Platform

## Overview

RelateAI is an AI-powered relationship communication platform that helps couples communicate more effectively through mediated conversations. The application features a "Dr. Ponz" AI mediator that intercepts potentially inflammatory messages and reframes them constructively before delivery to the partner. Key features include:

- User authentication with partner invite system
- Relationship compatibility quiz
- "Airlock" feature for mindful message preparation with breathing exercises
- Real-time mediated chat between partners
- Relationship insights dashboard with synapse visualization

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Routing**: Wouter (lightweight router)
- **State Management**: TanStack React Query for server state
- **Styling**: Tailwind CSS v4 with custom theme variables
- **UI Components**: shadcn/ui component library (New York style) with Radix UI primitives
- **Animations**: Framer Motion for transitions and visual effects
- **Fonts**: Outfit (display/headers) and DM Sans (body text)

### Backend Architecture
- **Runtime**: Node.js with Express
- **Language**: TypeScript with ES modules
- **API Pattern**: RESTful JSON APIs under `/api` prefix
- **Build System**: Custom build script using esbuild (server) and Vite (client)
- **Development**: Hot module replacement via Vite middleware

### Data Layer
- **Database**: PostgreSQL via Neon serverless
- **ORM**: Drizzle ORM with drizzle-zod for validation
- **Schema Location**: `shared/schema.ts` (shared between client and server)
- **Tables**: users, couples, quiz_responses, chat_sessions, messages, airlock_entries

### Authentication
- **Password Hashing**: bcrypt with 10 salt rounds
- **Session Strategy**: Cookie-based sessions
- **Partner Linking**: Invite code system for couple pairing

### AI Integration
- **Provider**: OpenAI-compatible API (configurable base URL)
- **Primary Use**: Message mediation through "Dr. Ponz" system prompt
- **Response Format**: Structured JSON with mediated text, sentiment analysis, and explanations

### Project Structure
```
├── client/           # React frontend
│   ├── src/
│   │   ├── components/  # UI components
│   │   ├── pages/       # Route pages
│   │   ├── hooks/       # Custom React hooks
│   │   └── lib/         # Utilities and API client
├── server/           # Express backend
│   ├── index.ts      # Server entry point
│   ├── routes.ts     # API route definitions
│   ├── storage.ts    # Database operations
│   └── vite.ts       # Vite dev server integration
├── shared/           # Shared code
│   └── schema.ts     # Drizzle database schema
└── migrations/       # Database migrations
```

## External Dependencies

### Database
- **Neon PostgreSQL**: Serverless Postgres database
- **Connection**: Via `DATABASE_URL` environment variable
- **WebSocket**: Required for Neon serverless driver

### AI Services
- **OpenAI API**: Message mediation and analysis
- **Environment Variables**: 
  - `AI_INTEGRATIONS_OPENAI_BASE_URL`
  - `AI_INTEGRATIONS_OPENAI_API_KEY`

### Key NPM Packages
- `@neondatabase/serverless`: Database connectivity
- `drizzle-orm` / `drizzle-kit`: ORM and migrations
- `openai`: AI API client
- `bcrypt`: Password hashing
- `express`: HTTP server
- `@tanstack/react-query`: Data fetching
- `framer-motion`: Animations
- `wouter`: Client-side routing