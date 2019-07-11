# rainbowtext
A mini Flask App to demonstrate auto deploy to AWS-ECS Fargate with Docker-Compose

Project Structure.
```
- nginx
    | - check.sh
    | - dockerfile
    | - nginx.conf
    | - nginx.dev.conf
- scripts
    | - .env (ignored)
    | - config_ecr.py
    | - del_ecr.py
    | - deploy.sh
    | - destroy.sh
    | - login_ecr.sh
    | - set_ecs_params.py
    | - setup_ecs.sh
    | - task-execution-assume-role.json
- templates
    | - home.html
- .gitignore
- app.py
- docker-compose.ecs.yml(generated and ignored)
- docker-compose.yml
- dockerfile
- ecs-params.yml
- ecs-params.ecs.yml (generated and ignored)
- instructions.txt
- LICENSE
- README.md
- requirements.txt
- uwsgi.ini
```

`.env` content, this should be placed in your `scripts` folder.
*run `source .env` to load your environment variables*
```shell
export AWS_ACCOUNT_ID=AWS_ACCOUNT_ID
export AWS_REGION=us-east-1

export DOCKER_COMPOSE_YML_INPUT=docker-compose.yml
export DOCKER_COMPOSE_YML_OUTPUT=docker-compose.ecs.yml

export ECS_PARAMS_INPUT=ecs-params.yml
export ECS_PARAMS_OUTPUT=ecs-params.ecs.yml

export AWS_ACCESS_KEY_ID=AWS_ACCESS_KEY_ID
export AWS_SECRET_ACCESS_KEY=AWS_SECRET_ACCESS_KEY

```


This project makes use of Docker to automate deployment to AWS ECS FARGATE.

### Build for production and deploy
```
docker-compose build --build-arg build_env="production" && ./scripts/deploy.sh
```

### Build locally
```
docker-compose build && docker-compose up
```

### Deploy to ECS FARGATE
```
scripts/deploy.sh
```

### Destroy after testing app
```
scripts/destroy.sh
```