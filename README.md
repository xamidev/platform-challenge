# DevOps Platform Challenge — Starter

## Project purpose

The purpose of this project is to learn more about GitHub, workflows, CI/CD, Docker, and Terraform, and to work on a practical example of what we will do in a real work environment, working as a team.

## Architecture

The app's source code is located in `src/app.js`.  
The app's tests are located in the `tests` folder.
The application listens on port 3000.

The endpoints are:

- `GET /`
- `GET /tasks`, fetches all the tasks
- `POST /tasks`, allows a user to create a task with parameter `title`
- `PATCH /tasks/:id`, allows a user to mark a task as completed
- `GET /health`, used to see if the app is alive
- `GET /total`, allows a user to calculate the total price of items in a hardcoded basket.
- `DELETE /tasks/:id`, allows a user to delete some task with its ID

## Local setup

Have a compatible (recent, 18/20/22) Node.js version installed, which supports Express. Preferably run the project on a Unix-based machine with a terminal.

## Tests 

Clone the repo, then run locally:

```bash
npm install
npm test
```

## Docker usage

With the Docker engine installed on your machine, run the following commands. Docker Compose is not required here.

```
docker build -t devops-platform-challenge .
docker run --rm -p 3000:3000 devops-platform-challenge
```

## CI/CD

The CI is split in a couple of different workflow files, located in `.github/workflows/`. They are as following:

- `node-ci.yml` runs all of the tests on the application. It is required for tests to pass before merging. This workflow also checks the dependencies for vulnerabilities.
- `docker.yml` makes a Docker image from our application's code and publishes it on ghcr.io
- `terraform.yml` only checks the Terraform config syntax and format.

## Terraform

Terraform is here only to satisfy our CI requirement and to establish a structure that could later be expanded if infrastructure were introduced.

## Development workflow

We worked as a team of four. Each team member, in order to add a new feature or fix a bug, is required to go through a complete workflow:  

**Issue → Branch → Code → Pull Request → Review → Approval → Merge → CI → Container → Package → Infrastructure validation**
