# Personal Finance Advisor Bot

An AI-assisted personal finance web app built with **Flask**, **SQLAlchemy** and an AI advisory engine.
Log income and expenses, get a personalised budget plan, track savings goals and view monthly reports.

## Features
- User accounts with a profile type: salaried, student, freelancer or household
- Income and categorised expense logging
- Budget generation (50/30/20 adapted per profile; freelancers budget from recent lower-income months)
- Overspending detection and saving recommendations
- Savings goals with progress tracking and an emergency-fund target
- Monthly report (HTML at `/report`, JSON at `/api/report`)
- AI advice: uses Claude when `ANTHROPIC_API_KEY` is set, otherwise a built-in rule-based engine

## Project structure
```
app/
  __init__.py     app factory
  models.py       User, Income, Expense, Goal
  analysis.py     summaries, budgets, overspending, lean-month detection
  advisor.py      LLM + rule-based recommendations
  routes.py       web routes and JSON API
  templates/      Jinja2 pages
tests/            pytest suite
config.py, run.py
```

## Setup
```bash
git clone <your-repo-url> && cd finance-advisor-bot
python -m venv venv && source venv/bin/activate   # Windows: venv\Scripts\activate
pip install -r requirements.txt
cp .env.example .env                              # set SECRET_KEY, optional ANTHROPIC_API_KEY
python run.py                                     # http://127.0.0.1:5000
```
Run tests: `pytest`

## Usage scenarios
| Profile | Behaviour |
|---|---|
| Salaried | 50/30/20 budget, overspending alerts, monthly summary |
| Student | 60/25/15 budget suited to a fixed allowance |
| Freelancer | Budget based on recent lean income, 30% savings target, low-savings months flagged |
| Household | 60/20/20 budget, focus on groceries, utilities, education, healthcare |

## Future enhancements
Predictive spending analytics, investment suggestions, richer goal tracking, financial health scoring.

## License
MIT
