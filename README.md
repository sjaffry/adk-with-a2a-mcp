# Description
AI Agents built with ADK with A2A and MCP

# Deployemnt
These agents can be deloyed on both Agent Engine or GKE

## Agent Engine
Run the following CLI commands from the root directory of each agent.

```bash
cd plotwriter

adk deploy agent_engine --project [YOUR PROJECT NAME] --region [REGION] movie_plotwriter

cd researcher

adk deploy agent_engine --project [YOUR PROJECT NAME] --region [REGION] wiki_researcher
```

## GKE

### Build & push container images
```bash
cd plotwriter

docker build -t [REGION]-docker.pkg.dev/[GCP-PROJECT-ID]/[REPO-NAME]/researcher-agent:latest .

docker push [REGION]-docker.pkg.dev/[GCP-PROJECT-ID]/[REPO-NAME]/researcher-agent:latest

cd researcher

docker build -t [REGION]-docker.pkg.dev/[GCP-PROJECT-ID]/[REPO-NAME]/plotwriter-agent:latest .

docker push [REGION]-docker.pkg.dev/[GCP-PROJECT-ID]/[REPO-NAME]/plotwriter-agent:latest
```

### Deploy to GKE
```bash
cd plotwriter/K8s
kubectl apply -f Deployment.yaml

cd researcher/K8s
kubectl apply -f Deployment.yaml
```