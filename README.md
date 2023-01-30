# Kubernetes-demo-application

## Project structure:

```

├── app                   # Base directory
│   ├── crud.py           # Crud Logic 
│   ├── database.py       # Database engine
│   ├── main.py           # API endpoints and FastAPI initialization
│   ├── models.py         # Database models
│   └── schemas.py        # Schemas used to exchange data in API
├── docker-compose.yaml   # docker-compose with web and postgres
├── Dockerfile            # Dockerfile for FastAPI application
└── requirements.txt      # Requirements for project
```

## Install and run:

Clone the project:

```bash
git clone git@github.com:vjanz/kubernetes-demo-app.git
```

Copy .env.example to .env

```bash
cp .env.example .env
```

Start the project with docker-compose:

```bash
docker-compose up -d --build
```

### Visit the application:

http://localhost:8000/api/docs

#### Create a user

```
curl -X 'POST' \
'http://localhost:8000/users/' \
  -H 'Content-Type: application/json' \
-d '{
"email": "test@demo.com",
"password": "somepassword"
}'
------------------------------------------------------------
{"email":"test@demo.com","id":1,"is_active":true,"items":[]}  
```

#### Create an item for user

```
curl -X 'POST' \
'http://0.0.0.0:8000/users/1/items/' \
-H 'Content-Type: application/json' \
-d '{
"title": "Item1",
"description": "Some Description"
}'

Excepted response:
{"title":"Item1","description":"Some Description","id":1,"owner_id":1} 
```
