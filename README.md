# AWS Infrastructure Automation with Ansible & Docker ☁️🐳

This project demonstrates a complete DevOps workflow for deploying web services (Nginx) and databases (MySQL) on AWS EC2 instances. 
The project evolves from a basic native installation to a fully containerized environment using Docker, managed by **Ansible Roles**.

## 🚀 Project Overview

The goal was to provision two EC2 instances on AWS and deploy specific services based on their tags. The project is divided into three evolutionary stages:

1.  **Stage 1: Native Deployment** - Installing services directly on the OS.
2.  **Stage 2: Docker Transition (Bonus)** - Containerizing the services.
3.  **Stage 3: Refactoring to Roles (Best Practice)** - Organizing code into modular Ansible Roles.

---

## 🛠️ Architecture & Features

* **Dynamic Inventory:** Uses `aws_ec2.yml` to dynamically fetch instances based on tags.
* **Tag-Based Logic:** Deploys Nginx or MySQL based on AWS Tags (`Service`, `DockerImage`).
* **Containerization:** Automated Docker installation and container orchestration.
* **Scheduled Tasks:** Configures a Cron Job for scheduled server restarts based on AWS tags.
* **Security:** Handles Ubuntu 24.04 `externally-managed-environment` restrictions using `apt` instead of `pip`.

---

## 📂 Repository Structure

```text
.
├── README.md                   # Project documentation
├── ansible.cfg                 # Ansible configuration
├── aws_ec2.yml                 # AWS Dynamic Inventory plugin
├── my-key.pem                  # SSH Key (Excluded in real repos)
│
├── site.yml                    # STAGE 1: Native installation playbook
├── site_docker.yml             # STAGE 2: Monolithic Docker playbook
├── site_roles.yml              # STAGE 3: Master playbook using Roles
│
└── roles/                      # Modular Roles (Best Practice)
    ├── common/                 # Setup (Hostname, Owner verification)
    ├── docker/                 # Infrastructure (Docker engine installation)
    └── app_deploy/             # Application (Container logic & Cron jobs)
