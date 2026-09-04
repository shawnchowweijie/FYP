# NTU Final Year Project - CI/CD for Application(?)
### Name: Chow Wei Jie Shawn
### FYP ID: CCDS26-0155
### Project Title: Application(?): Automated CI/CD Pipeline and Deployment Automation
### Supervisor: Prof Chng Eng Siong

### Start Date: 4 Sept 2026
### End Date: TBC

## Project links
- [Project Plan](FYP_Project_Plan_ShawnChowWeiJie.pdf)

## Project overview
Application(?) is a system developed and maintained by successive Final Year Project students and researchers in the NTU Speech Lab. While the application itself is functional, its software delivery process remains manual: builds and deployments are run by hand on a specific machine, there is no automated testing, and configuration values and credentials are stored in plaintext files. As a result, releases are slow and error-prone, the version currently deployed is difficult to determine, and there is no straightforward way to roll back a faulty release.

This project designs and implements an automated Continuous Integration and Continuous Deployment (CI/CD) pipeline for ApplicationX, so that changes can be built, verified and deployed in a consistent and repeatable manner without manual intervention. A previous Final Year Project ([Sih Jia Qi, "CI/CD for Automatic Speech Recognition System"](https://github.com/sihjiaqi/ntu-fyp-asr-cicd/blob/main/FYP_May2026_SihJiaQi.pdf)) introduced a CI/CD pipeline for another system in the NTU Speech Lab and demonstrated that this approach works well in this environment. This project applies the same approach to ApplicationX, and extends it in four areas that were not covered previously: an automated test suite enforced as a quality gate before any change can be merged; handling of database schema changes as a controlled step in the deployment process; a containerised development environment that allows a future student to run the entire system with a single command; and a rollback procedure that is verified by deliberately deploying a faulty build.

## Limitations of the current system
- Manual builds and deployments that are error-prone and hard to roll back.
- No automated testing.
- Configuration values and credentials stored in plaintext files.
- Slow, error-prone releases, with the currently deployed version difficult to determine.
- No straightforward way to roll back a faulty release.

## Proposed improvements
- **Continuous Integration**: GitHub Actions workflow triggered on every pull request and merge; code linting and formatting checks; an automated test suite (unit and integration) enforced as a quality gate with a minimum coverage threshold; source code, dependency and container image scanning for vulnerabilities and exposed secrets; automated dependency update proposals; versioned container images built and published to a registry.
- **Containerisation**: Dockerfiles for each service so the application builds and runs identically in development and deployment; a Docker Compose configuration that starts the entire system, including its database and dependent services, with a single command.
- **Continuous Deployment**: A Kubernetes (k3s) cluster on laboratory hardware, with an equivalent local cluster for development; each service packaged as a Helm chart with separate development/production configuration; Argo CD to automatically synchronise the cluster with the deployment repository using Git as the single source of truth; Sealed Secrets so no credential is committed in plaintext; database schema migrations as a controlled, rollback-documented deployment step; progressive rollouts with automatic rollback on failed health checks.
- **Monitoring**: Prometheus and Grafana, exposing application metrics with dashboards for request rate, error rate, response time and resource usage, and threshold-based alerting.

## Proposed technology stack
- **Version control & CI**: Git, GitHub, GitHub Actions
- **Automated testing**: pytest, code coverage reporting
- **Containerisation**: Docker, Docker Compose
- **Container registry**: GitHub Container Registry
- **Security scanning**: Trivy, Dependabot
- **Orchestration & packaging**: Kubernetes (k3s), Helm
- **Continuous deployment**: Argo CD, Argo Rollouts
- **Secret management**: Sealed Secrets
- **Monitoring**: Prometheus, Grafana

All tools above are open source and self-hostable, so the pipeline does not depend on a commercial cloud provider.

## Stretch goals
- **Preview environments**: automatically create a temporary environment for each pull request, removed when the pull request is closed.
- **Backup and recovery**: an automated, tested backup and restore procedure for the database and stored files.

## Roadmap / Milestones
* Phase 1 — Preparation (25 Aug 2026 – 12 Oct 2026): scope definition, review of the existing system, pipeline design
* Phase 2 — Containerisation & CI (12 Oct 2026 – 21 Dec 2026): Dockerfiles, Docker Compose, GitHub Actions, automated testing
* Phase 3 — Kubernetes & Continuous Deployment (21 Dec 2026 – 22 Feb 2027): Helm charts, Argo CD, Sealed Secrets, schema migrations, rollback verification
* Phase 4 — Monitoring & Evaluation (22 Feb 2027 – 19 Apr 2027): Prometheus/Grafana, evaluation, buffer time, stretch goals

<img width="2752" height="1502" alt="unnamed" src="https://github.com/user-attachments/assets/b4e31f16-dbd8-4c7b-a3c2-81c4ab7c8918" />

## Video Updates

Playlist:

[YouTube Playlist](link)

## Contact
* **Email**: [shawnchowweijie@gmail.com](shawnchowweijie@gmail.com)
* **LinkedIn**: [linkedin.com/in/shawn-chow-938b662b3/](https://www.linkedin.com/in/shawn-chow-938b662b3/)

## References
- [Sih Jia Qi, "CI/CD for Automatic Speech Recognition System" (NTU FYP, May 2026)](https://github.com/sihjiaqi/ntu-fyp-asr-cicd/blob/main/FYP_May2026_SihJiaQi.pdf) — prior NTU Speech Lab FYP that this project's CI/CD approach builds on
