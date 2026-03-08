# GitHub Actions: Zero to Hero

A hands-on repo to learn GitHub Actions from scratch. Each workflow covers a real-world concept — start from the top and work your way down.

## What's Inside

This repo contains a **Flask web app** with a full CI/CD pipeline built entirely using GitHub Actions.

```
app.py                  → Flask app (source code)
Dockerfile              → Container image definition
docker-compose.yml      → Production deployment config
templates/index.html    → App frontend
index.html              → Portfolio static site
```

## Workflows

| # | Workflow | Concepts Covered | What It Does |
|---|---------|-----------------|-------------|
| 1 | [Hello](.github/workflows/hello.yml) | `on: push`, branch filters, path filters, multiple jobs, runners | Runs echo commands when HTML files are pushed to main — your first workflow |
| 2 | [CICD](.github/workflows/cicd.yml) | `workflow_dispatch`, manual inputs, `needs` (job dependencies), `if` conditionals | Simulates a CI/CD pipeline (code → build → test → deploy) triggered manually with environment selection |
| 3 | [Portfolio Deploy](.github/workflows/portfolio-deploy.yml) | GitHub Pages, `permissions`, pre-built actions, environments, deployment URLs | Deploys a static site to GitHub Pages using official actions |
| 4 | [Python Lint](.github/workflows/python-matrix.yml) | Matrix strategy, `fail-fast`, `actions/setup-python`, dependency install | Lints `app.py` with flake8 across Python 3.9–3.13 in parallel |
| 5 | [Docker Build & Push](.github/workflows/docker-build-push.yml) | Docker login, build & push actions, `secrets`, `vars`, image tagging | Builds a Docker image and pushes to Docker Hub with branch, latest, and SHA tags |
| 6 | [Deploy App](.github/workflows/deploy-app.yml) | `workflow_run` (chained workflows), self-hosted runners, Docker Compose, environment variables | Auto-deploys the Flask app on a self-hosted server after Docker image is pushed |

## Concepts Cheat Sheet

| Concept | Where to Find It |
|---------|-----------------|
| Push trigger | [hello.yml](.github/workflows/hello.yml) |
| Path filters | [hello.yml](.github/workflows/hello.yml) |
| Manual trigger (`workflow_dispatch`) | [cicd.yml](.github/workflows/cicd.yml) |
| Input parameters (choice) | [cicd.yml](.github/workflows/cicd.yml) |
| Job dependencies (`needs`) | [cicd.yml](.github/workflows/cicd.yml) |
| Conditional execution (`if`) | [cicd.yml](.github/workflows/cicd.yml), [deploy-app.yml](.github/workflows/deploy-app.yml) |
| Permissions | [portfolio-deploy.yml](.github/workflows/portfolio-deploy.yml) |
| Environments & deployment URLs | [portfolio-deploy.yml](.github/workflows/portfolio-deploy.yml) |
| Matrix strategy | [python-matrix.yml](.github/workflows/python-matrix.yml) |
| Secrets & variables | [docker-build-push.yml](.github/workflows/docker-build-push.yml) |
| Chained workflows (`workflow_run`) | [deploy-app.yml](.github/workflows/deploy-app.yml) |
| Self-hosted runners | [deploy-app.yml](.github/workflows/deploy-app.yml) |
| Docker Compose deploy | [deploy-app.yml](.github/workflows/deploy-app.yml) |

## Getting Started

1. **Fork this repo**
2. **Set up secrets** — Go to repo Settings → Secrets and Variables → Actions:
   - Secret: `DOCKERHUB_TOKEN` (your Docker Hub access token)
   - Variable: `DOCKERHUB_USER` (your Docker Hub username)
3. **Push to main** — workflows 1, 4, and 5 will trigger automatically
4. **Try manual trigger** — go to Actions tab → CICD → Run workflow
5. **Read each workflow file** — they are commented for learning

## Repo Structure

```
.
├── .github/workflows/
│   ├── hello.yml              # 1. Basics
│   ├── cicd.yml               # 2. Manual CI/CD pipeline
│   ├── portfolio-deploy.yml   # 3. GitHub Pages
│   ├── python-matrix.yml      # 4. Matrix testing
│   ├── docker-build-push.yml  # 5. Docker CI
│   └── deploy-app.yml         # 6. Docker CD
├── templates/
│   └── index.html             # Flask template
├── app.py                     # Flask application
├── Dockerfile                 # Container definition
├── docker-compose.yml         # Compose config
├── index.html                 # Portfolio static site
├── requirements.txt           # Python dependencies
└── CNAME                      # Custom domain for GitHub Pages
```
