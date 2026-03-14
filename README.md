# DevSecOps CI/CD Pipeline – Secure Flask Application 🚀

This project demonstrates a **DevSecOps CI/CD pipeline** that integrates multiple security and quality checks before building and deploying a Dockerized Flask application using **GitHub Actions (GitHub hosted runners)**.

The pipeline follows a **security-first approach** where code quality, secrets detection, dependency vulnerabilities, and Dockerfile issues are validated before the build stage.

---

# 📌 Pipeline Workflow

The pipeline follows this execution order:

```
Code Push
   ↓
Code Quality Check (Flake8)
   ↓
Secrets Scan
   ↓
Dependency Vulnerability Scan
   ↓
Dockerfile Lint Check
   ↓
Docker Image Build
   ↓
Trivy Image Security Scan
   ↓
DockerHub Push
   ↓
Deployment
```

---

# ⚙️ Technologies Used

## Application

* Python
* Flask

## DevOps Tools

* GitHub Actions (GitHub Hosted Runner)
* Docker
* DockerHub

## Security Tools

* Flake8 → Code quality check
* Bandit → Python security scan
* Safety → Dependency vulnerability scan
* Trivy → Container vulnerability scanner
* GitHub Secrets Detection

---

# 🔍 DevSecOps Security Stages

## Pre-Build Security Gates

Before Docker build starts, the pipeline runs mandatory checks:

### Code Quality Check

```
flake8 app.py
```

Ensures:

* Clean code structure
* No syntax issues
* Python best practices

---

## Secrets Scan

Detects:

* Hardcoded credentials
* API keys
* Tokens
* Sensitive configuration

---

## Dependency Scan

Checks Python packages for:

* Known CVEs
* Vulnerable versions
* Security advisories

Example:

```
safety check
```

---

## Dockerfile Security Check

Validates Dockerfile best practices:

* Base image security
* Layer optimization
* Security misconfiguration
* Best practices compliance

---

# 🐳 Build Stage

After all checks pass:

Docker image is built:

---

# 🔐 Container Security Scan

After build, Trivy scans the Docker image:

Detects:

* OS vulnerabilities
* Library vulnerabilities
* Critical CVEs
* Misconfigurations

```

Pipeline fails if critical vulnerabilities are found.

```

# 🚀 Deployment Stage

After successful scans:

Pipeline performs:

* Docker image tagging
* DockerHub push
* Container deployment

Deployment:

docker compose up -d --build
```
