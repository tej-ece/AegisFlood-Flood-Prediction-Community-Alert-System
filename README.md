# AegisFlood (MVP)

AI-powered flood prediction and community alert system.

This repository contains a TypeScript React frontend and a FastAPI backend per the MVP scope:
- Citizen registration and dashboard (risk view)
- Authority dashboard (basic)
- Simple prediction logic
- SMS alerts via Twilio (mockable)
- JWT auth with roles (citizen, authority)

## Project Structure

```
.
├── backend/
│   ├── app/
│   │   ├── main.py
│   │   ├── database.py
│   │   ├── models.py
│   │   ├── schemas.py
│   │   ├── auth.py
│   │   ├── prediction.py
│   │   ├── alerts.py
│   │   └── admin.py
│   ├── data/
│   │   └── regions.json
│   ├── scripts/
│   │   ├── setup_db.py
│   │   └── load_regions.py
│   ├── requirements.txt
│   └── .env.example
├── frontend/
│   ├── index.html
│   ├── package.json
│   ├── tsconfig.json
│   ├── tsconfig.node.json
│   ├── vite.config.ts
│   ├── tailwind.config.js
│   ├── postcss.config.js
│   └── src/
│       ├── main.tsx
│       ├── App.tsx
│       ├── styles/main.css
│       ├── components/
│       │   ├── shared/{Button.tsx,Card.tsx,Input.tsx,StatusPill.tsx,Toggle.tsx}
│       │   └── ui/{Header.tsx,NavigationBar.tsx,DashboardCard.tsx}
│       ├── pages/{Home.tsx,Dashboard.tsx,Login.tsx,Registration.tsx,Settings.tsx}
│       ├── context/AuthContext.tsx
│       └── services/api.ts
├── docker-compose.yml
└── .gitignore
```

## Quick Start (Local)

### Backend
1) Copy env
```
cp backend/.env.example backend/.env
```
2) Start Postgres + API
```
docker-compose up -d postgres
python -m venv .venv && .venv/Scripts/activate
pip install -r backend/requirements.txt
python backend/scripts/setup_db.py
python backend/scripts/load_regions.py
uvicorn backend.app.main:app --reload
```

API: http://localhost:8000, Docs: http://localhost:8000/docs

### Frontend
```
cd frontend
npm install
npm run dev
```

App: http://localhost:5173

## Security (MVP)
- JWT with 24h expiry, role-based access control
- Input validation via Pydantic schemas
- CORS restricted via FRONTEND_ORIGIN
- Env-based secrets, no secrets in code
- Twilio credentials via env, optional mock mode

## Notes
- This is MVP scope only. Extended features are out-of-scope until requested.

# My Contribution 
- Trained and compared multiple ML models for flood prediction:
  LSTM (98% accuracy), Random Forest, Logistic Regression, KNN
- Selected best performing model based on accuracy comparison
- Contributed to the core prediction engine of the system


