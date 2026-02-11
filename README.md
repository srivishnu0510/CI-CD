**CI/CD Pipeline with Jenkins, Terraform, and Ansible on AWS**

**Overview**
This project implements an automated and scalable CI/CD Pipeline using Jenkins, Terraform, and Ansible on AWS.
The pipeline provisions AWS infrastructure using Terraform, configures EC2 instances using Ansible’s dynamic inventory, and deploys Nginx as the application server.
It also integrates Auto Scaling with an Application Load Balancer (ALB) to ensure high availability and production-grade performance.

**Features**
-Fully automated Infrastructure as Code (IaC) using Terraform
-Dynamic configuration management using Ansible Dynamic Inventory
-CI/CD pipeline integrated with Jenkins
-Scalable AWS setup with EC2, VPC, Auto Scaling Group, ALB
-Nginx deployment using Ansible
-Logging & monitoring via CloudWatch
-GitHub integration for version-controlled deployments

**Tech Stack**
-CI/CD: Jenkins
-IaC: Terraform
-Configuration Management: Ansible
-Cloud: AWS (EC2, VPC, ALB, ASG, IAM, CloudWatch)
-Version Control: Git & GitHub
-Scripting: Linux, Bash
-Web Server: Nginx

**Project Flow**
-Developer pushes code → GitHub
-Jenkins pipeline triggers automatically
-Terraform provisions AWS environment
-Terraform outputs are passed to Ansible dynamic inventory
-Ansible installs Nginx on EC2 instances
-ASG + ALB ensure high availability
-CloudWatch monitors metrics and logs

**Prerequisites**
-AWS Account
-IAM Role with EC2, VPC, ALB, ASG, S3, IAM permissions
-Jenkins with required plugins:GitHub,Terraform,Ansible,Pipeline
-Terraform & Ansible installed
-SSH key pair for EC2

**Repository Structure**
.
├── jenkins-pipeline
│   └── Jenkinsfile
├── terraform
│   ├── main.tf
│   ├── variables.tf
│   ├── outputs.tf
│   └── provider.tf
├── ansible
│   ├── playbook.yml
│   ├── roles/
│   │   └── nginx/
│   │       ├── tasks/main.yml
│   │       └── templates/
│   └── dynamic-inventory.py
└── README.md


**Jenkins Pipeline Stages**
1. Checkout Stage-Pulls latest code from GitHub
2. Terraform Init & Apply-Provisions VPC, Subnets, EC2, ALB, Auto Scaling Group,Outputs instance IPs to dynamic inventory
3. Ansible Provisioning-Installs Nginx,Configures firewall and service
4. Health Check-Verifies Nginx is reachable through ALB

**Terraform Execution**
terraform init
terraform plan
terraform apply -auto-approve

**Ansible Execution**
ansible-playbook -i dynamic-inventory.py playbook.yml

**Expected Output**
-A fully functional CI/CD pipeline
-Auto-scaling infrastructure
-Load-balanced Nginx deployment
-Automated provisioning + configuration
-CloudWatch monitoring enabled

**Future Enhancements**
-Integrate Docker + ECR
-Kubernetes migration (EKS)
-Blue-Green / Canary Deployments
-Add Vault for secrets management


Author
Sri Vishnu
Cloud & DevOps Engineer
