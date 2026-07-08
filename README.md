# Project 1 — Products API (Demo)

A minimal Django + Django REST Framework project exposing CRUD endpoints for a `Product` catalog. Built for demonstration/learning purposes.

## Tech Stack

- Django 6.0
- Django REST Framework
- PostgreSQL

## Project Structure

- `project_1/` — Django project config (settings, root URLs, WSGI/ASGI)
- `products/` — app containing the `Product` model, serializer, viewset, and admin registration

## Setup

1. Install dependencies:
   ```bash
   pip install django djangorestframework psycopg2-binary python-dotenv
   ```
2. Configure `.env` in the project root with your Postgres credentials:
   ```
   DB_NAME=test_db
   DB_USER=postgres
   DB_PASSWORD=your_password
   DB_HOST=localhost
   DB_PORT=5432
   ```
3. Run migrations:
   ```bash
   python manage.py migrate
   ```
4. Start the dev server:
   ```bash
   python manage.py runserver
   ```

## Routes

| URL | Description |
|---|---|
| `/` | Simple homepage (plain text welcome message) |
| `/admin/` | Django admin site |
| `/api/products/` | Products CRUD API |

## API Endpoints

Base path: `/api/products/`

| Method | URL | Action |
|---|---|---|
| GET | `/api/products/` | List all products |
| POST | `/api/products/` | Create a product |
| GET | `/api/products/{id}/` | Retrieve one product |
| PUT | `/api/products/{id}/` | Full update |
| PATCH | `/api/products/{id}/` | Partial update |
| DELETE | `/api/products/{id}/` | Delete a product |

### Product fields

`id`, `name`, `description`, `price`, `quantity`, `created_at`, `updated_at`

Built via DRF's `ModelViewSet` + `DefaultRouter` — no custom business logic beyond default ordering (`-created_at`).

## Admin Access (Demo Credentials)

> ⚠️ Demo project only — do not reuse these credentials anywhere real.

- URL: `http://127.0.0.1:8000/admin/`
- Username: `admin`
- Password: `Admin@12345`

## Notes

- `DEBUG = True` and no authentication/permissions are set on the API — all CRUD endpoints are open to anyone. Fine for local demo use only, not production-ready.
- No automated tests are implemented yet.
