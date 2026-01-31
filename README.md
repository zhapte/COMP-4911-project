# COMP4911 Timesheet System

## Overview
This project is a web-based information system to support software project management.  
It allows employees to submit weekly timesheets and allows managers/admins to track project effort, work packages, and generate reports.

Course: COMP4911  
Instructor/Sponsor: Bruce Link  



## Tech Stack

### Frontend
- ASP.NET Core Razor Pages  
- Purpose: Web UI for employees and managers

### Backend
- Jakarta EE REST API (WildFly)  
- EJB service layer planned for future iterations

### Database
- SQL Database 

### Deployment
- OKD / OpenShift (container-based deployment)


## Repository Structure

```text
├── frontend/    # .NET client application
├── backend/     # Jakarta EE backend (EJB + REST)
├── Sql/         # SQL scripts and schema files
├── tests/       # Any test code for front end or back end
├── docs/        # Any documentation for the project
└── README.md
```


## Rest Endpoint

- `GET /api/greet`


## Development Setup

### Prerequisites
Install the following tools:

- .NET SDK 8.0+
- Java JDK 17+
- Maven
- WildFly
- Git


## Frontend Setup (.NET Razor Pages)

Run the frontend locally:

`cd frontend`
`dotnet watch`

Frontend runs at:

http://localhost:3000


## Backend Setup (Jakarta REST)

Build the backend:

`cd backend`
`mvn clean wildfly:dev`

Test endpoint:

http://localhost:8080/Project/api/greet


## Database Setup

TBD


## Running Both Together

1. Run the backend:
cd backend
mvn clean wildfly:dev

2. Confirm `/api/greet` works in browser or Postman 

3. Start Razor frontend:

cd frontend
dotnet watch

4. open:

http://localhost:3000

Frontend should display the backend response.


## Team Rules and Standards

- Use meaningful names and keep code readable
- Never push directly to main
- Prefer small PRs that are easy to review
- Use meaningful variable and class names
- Keep REST endpoints small business logic belong in service/EJB layer

### Branching
- main → stable release branch  
- dev → active development branch  
- Feature branches:
- Always create a feature branch:

  feature/<task-name>

- Examples:

  feature/login  
  feature/timesheet-entry  
  bugfix/api-routing  

- Open a Pull Request (PR) before merging


### Pull Requests
- PR must include a clear description of changes
- Assign all reviewers listed here
- PR should be small and focused
All pull requests must be reviewed by:

- Kaid  @kaid711
- Nate  @NateRolo 
- Lucas @zhapte


### Naming Conventions

Backend (Java)
- Classes: PascalCase  
- Methods: camelCase  
- REST routes: `/api/resource-name`

Frontend (.NET)
- Pages: PascalCase.cshtml  
- PageModels: PascalCase.cshtml.cs  
- Variables: camelCase


### Commit Message Guidelines

Good examples:
- Add hello world endpoint
- Setup Razor Pages frontend
- Fix API base URL config

Bad examples:
- update stuff
- changes
- fix


### Folder Organization Rules

- frontend/ → all .NET Razor UI code
- backend/  → all Jakarta REST/EJB code
- sql/      → DB setup or deployment scripts
- tests/    → unit tests and integration tests for both frontend and backend 
- docs/		→ reports, diagrams, meeting notes 


### Documentation Rules

- Inline code formatting should be used in documentation:
  - Use `REST endpoints` instead of plain text
  - Use `dotnet run` when referencing commands
  - Use `GET /api/hello` when referencing routes
  
- Document all important endpoints in a simple list:

  - `POST /api/auth/login`
  - `GET /api/timesheets`
  - `POST /api/timesheets/submit`

- Add setup instructions directly in the README whenever something changes:
  - New environment variable
  - New required tool
  - New deployment step
  

## Authentication Plan

Planned approach:
- Token-based login (UUID stored in database)
- Token stored in HttpOnly cookie
- Role-based access control (Admin, Employee, Manager)


## Deployment Notes

