# Copilot instructions for this repository

## Project overview
This repository is a small FastAPI app for Mergington High School. It exposes a simple REST API and serves a static web UI for students to browse extracurricular activities and sign up for them.

## Repository structure
- `src/app.py`: FastAPI application entry point.
- `src/static/`: Browser UI assets (`index.html`, `styles.css`, `app.js`).
- `src/README.md`: App-specific usage notes and API docs.
- `.devcontainer/devcontainer.json`: Development container setup for Python 3.13 and port 8000.
- `.vscode/launch.json`: VS Code debug configuration for running the app with `uvicorn` reload mode.
- `.github/steps/`: Exercise instructions for the GitHub Copilot learning walkthrough.
- `requirements.txt`: Python dependencies.

## Tech stack and conventions
- Use Python 3.13+.
- Use FastAPI with `uvicorn` for local development.
- Keep the app simple: the current implementation stores activity data in memory.
- Data lives under the `activities` dictionary and is mutated directly in `src/app.py`.
- API routes should stay aligned with the browser client in `src/static/app.js` and with the docs in `src/README.md`.
- Prefer minimal, direct changes. Do not introduce heavy architecture or a database unless a task explicitly requires it.

## Key runtime behavior
- `GET /activities` returns the full activity catalog.
- `POST /activities/{activity_name}/signup` signs a student up for an activity using the `email` query parameter.
- Invalid activity names should return `404` with an `HTTPException`.
- The root route redirects to `/static/index.html`.
- Static files are served under `/static`.

## How to run the project
From the repository root:

```bash
pip install -r requirements.txt
uvicorn src.app:app --reload
```

Then open:
- http://localhost:8000/
- http://localhost:8000/docs

VS Code debug configuration is also available via the `Launch Mergington WebApp` launch target in `.vscode/launch.json`.

## Validation expectations
- Keep the app working as a lightweight web app with a static frontend and a FastAPI backend.
- Preserve the in-memory data model unless asked to change it.
- If editing behavior, validate the relevant route logic and ensure the frontend still works with the API contract.
- If tests are added, keep them focused on API behavior and signup validation.
