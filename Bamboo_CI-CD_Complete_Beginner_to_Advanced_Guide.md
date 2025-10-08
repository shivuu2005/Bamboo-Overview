# 🧩 Bamboo CI/CD – Complete Beginner to Advanced Practical Guide (DevOps Perspective)

## 🏁 Part 1: Introduction to Bamboo

| Concept | Description | Example |
|----------|--------------|----------|
| What is Bamboo? | Atlassian’s CI/CD tool for automating code build, test, and deployment pipelines. | Example: Automatically build and deploy a Java web app after every commit. |
| CI/CD Meaning | Continuous Integration (CI) ensures frequent code integration; Continuous Delivery (CD) automates deployment. | Jenkins, GitLab CI, and Bamboo are common CI/CD tools. |
| Why Bamboo? | Tight integration with Atlassian products (Bitbucket, JIRA, Confluence) and powerful agent-based scaling. | Build results automatically linked to JIRA issues. |

---

## ⚙️ Part 2: Bamboo Architecture Overview

**Visual Architecture:**

```
Developer → Bitbucket → Bamboo Server → Build Agents → Test → Deploy → Production
```

| Component | Function | Example |
|------------|-----------|----------|
| Bamboo Server | Central CI/CD management | Runs on `bamboo.company.com` |
| Agent | Executes builds and deployments | Remote Linux VM or AWS EC2 instance |
| Plan | Defines the build pipeline | “Build and Deploy Spring App” |
| Stage | Logical grouping of jobs | “Build”, “Test”, “Deploy” |
| Job | Unit of work inside a stage | “Run Maven Build” |
| Task | Command or operation in a job | “Execute Script”, “Upload Artifact” |

---

## 🧱 Part 3: Installation and Setup

| Step | Action | Example |
|------|---------|----------|
| 1 | Install Java (required) | `sudo apt install openjdk-11-jdk` |
| 2 | Download Bamboo | [https://www.atlassian.com/software/bamboo/download](https://www.atlassian.com/software/bamboo/download) |
| 3 | Configure database | MySQL / PostgreSQL supported |
| 4 | Start Bamboo server | `./start-bamboo.sh` |
| 5 | Access Web UI | `http://localhost:8085` |
| 6 | Configure license & admin | Atlassian account setup |

---

## 🧩 Part 4: How a Bamboo Build Plan Works

| Stage | Description | Example |
|--------|-------------|----------|
| Code Checkout | Pull code from repository | Bitbucket or GitHub |
| Build | Compile code | `mvn clean package` |
| Test | Run unit/integration tests | JUnit, pytest |
| Package | Create build artifact | `.jar`, `.war`, `.zip` |
| Deploy | Push artifact to environment | AWS EC2, Docker, Kubernetes |

**Visual Workflow:**

```
Code Push → Plan Trigger → Build Stage → Test Stage → Deploy Stage → Notify
```

---

## 🧠 Part 5: Creating a Plan (Step-by-Step Example)

| Step | Action | Description |
|------|---------|-------------|
| 1 | Create a New Plan | Name: “SpringApp-Build” |
| 2 | Connect Repository | Bitbucket repo |
| 3 | Add Stages | Build, Test, Deploy |
| 4 | Add Jobs/Tasks | “Run Maven Goal” → `clean install` |
| 5 | Add Deployment Project | Deploy to AWS EC2 or Docker |
| 6 | Save & Run | Bamboo triggers full pipeline |

---

## 🧩 Part 6: Agents in Bamboo

| Type | Description | Example Use |
|-------|-------------|--------------|
| Local Agent | Runs on Bamboo Server | For small projects |
| Remote Agent | Runs on external machine | Distributed build nodes |
| Elastic Agent | Cloud-hosted (AWS) | Auto-scale during heavy load |

**Visual:**

```
Bamboo Server
 ├─ Local Agent
 ├─ Remote Agent (VM)
 └─ Elastic Agent (AWS EC2)
```

---

## 🔗 Part 7: Integrations

| Tool | Purpose | Example |
|-------|----------|----------|
| Bitbucket | Source control & triggers | Auto-build on push |
| JIRA | Issue tracking | Build results linked to tickets |
| SonarQube | Code quality checks | Run static analysis post-build |
| Docker | Container builds | Build + push Docker image |
| Slack/Email | Notifications | Notify team on failure |

---

## 🌐 Part 8: Real-World Example – Flask Web App Deployment

**Scenario:** Deploying a Python Flask app using Bamboo CI/CD

1. Code pushed to Bitbucket triggers Bamboo.
2. Bamboo checks out code → installs dependencies.
3. Runs tests (`pytest`).
4. Packages app into Docker image.
5. Deploys to AWS ECS.
6. Sends Slack notification upon success.

**Result:** Fully automated build-test-deploy cycle for a Python app.

---

## 🧭 Part 9: Migration from Bamboo

| Migration Type | Description | Target Tool |
|----------------|--------------|--------------|
| Bamboo → Jenkins | Convert plans to Jenkinsfiles | Jenkins |
| Bamboo → GitLab CI | Rebuild plans in `.gitlab-ci.yml` | GitLab |
| Bamboo → GitHub Actions | YAML workflows replacing Bamboo plans | GitHub Actions |

**Mapping Example (Bamboo → GitHub Actions):**

| Bamboo | GitHub Actions |
|----------|----------------|
| Plan | Workflow |
| Stage | Job |
| Task | Step |
| Agent | Runner |

**Conversion Example:**

```yaml
# GitHub Actions equivalent
name: Build and Test
on: [push]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - run: mvn clean test
```

**Migration Tips:**
- Export plans via Bamboo REST API or Specs.
- Map Bamboo variables → environment variables.
- Test each pipeline incrementally.
- Archive logs and artifacts before switching tools.

---

## ⚡ Part 10: Scaling and Optimization

| Technique | Description | Example |
|------------|-------------|----------|
| Parallel Builds | Use multiple agents | Run 5 builds simultaneously |
| Caching | Reuse dependencies | Maven/Gradle cache |
| Artifact Sharing | Reuse compiled results | Avoid rebuilds |
| Branch Plans | Create per-branch builds | Build every feature branch |
| Scheduled Builds | Run periodic jobs | Nightly build triggers |

---

## 🧠 Part 11: Common Errors & Fixes

| Error | Cause | Fix |
|--------|--------|------|
| Agent offline | Connection issue | Restart agent service |
| Plan not triggered | No trigger rule | Add repository trigger |
| Build failed | Dependency issue | Check `pom.xml` or logs |
| DB connection failed | Wrong JDBC URL | Correct database config |

---

## 🔒 Part 12: Security & Best Practices

- 🔑 Use Bamboo Specs for version-controlled pipelines  
- 🔒 Configure SSL and role-based access control (RBAC)  
- 🔐 Use encrypted global variables for secrets  
- 🧱 Isolate build environments using Docker  
- 📬 Set up Slack/email alerts for build health  

---

## 🧾 Part 13: Visual Summary – Bamboo CI/CD Workflow

```
┌────────────────────────────────────────────┐
│ Developer pushes code to Bitbucket         │
└────────────────────────────────────────────┘
                │
                ▼
┌────────────────────────────────────────────┐
│ Bamboo detects change & starts build       │
└────────────────────────────────────────────┘
                │
                ▼
┌────────────────────────────────────────────┐
│ Build → Test → Package → Deploy → Notify   │
└────────────────────────────────────────────┘
```

---

## 🚀 Part 14: Comparison with Other CI/CD Tools

| Feature | Bamboo | Jenkins | GitHub Actions | GitLab CI |
|----------|---------|----------|----------------|
| UI | Modern Atlassian-style | Plugin-based | Minimal YAML | Advanced web UI |
| Integration | Bitbucket/JIRA | Plugin system | GitHub-native | GitLab-native |
| Config Format | GUI + Specs (Java DSL) | Groovy | YAML | YAML |
| Agents | Local, Remote, Elastic | Master-Agent | Runners | Runners |
| Scalability | High (via Elastic Agents) | Manual | Dynamic runners | Auto-scaling runners |

---

## 💡 Part 15: Key Takeaways

- Bamboo is ideal for teams using **Atlassian tools**.  
- Supports **hybrid and on-prem builds**.  
- Scales well with **Elastic Agents (AWS)**.  
- Migration to **GitHub Actions or GitLab** is straightforward using YAML.  
- Recommended for enterprise DevOps pipelines with strong traceability.  

---

## 📚 References

1. Atlassian Bamboo Official Docs – [https://confluence.atlassian.com/bamboo](https://confluence.atlassian.com/bamboo)  
2. Bamboo Specs (Infrastructure as Code) – [https://confluence.atlassian.com/bamboo/bamboo-specs-894743906.html](https://confluence.atlassian.com/bamboo/bamboo-specs-894743906.html)  
3. GitHub Actions Documentation – [https://docs.github.com/en/actions](https://docs.github.com/en/actions)  
4. GitLab CI/CD Pipelines – [https://docs.gitlab.com/ee/ci/](https://docs.gitlab.com/ee/ci/)  
5. Jenkins Pipeline Documentation – [https://www.jenkins.io/doc/book/pipeline/](https://www.jenkins.io/doc/book/pipeline/)  
6. Atlassian Bamboo Migration Guide – [https://confluence.atlassian.com/bamboo/migrating-data-to-bamboo-289277069.html](https://confluence.atlassian.com/bamboo/migrating-data-to-bamboo-289277069.html)

---

**Created by:** Shivam Malviya  
**Generated on:** 2025-10-08
**Version:** 1.0 (DevOps Focused Edition)
