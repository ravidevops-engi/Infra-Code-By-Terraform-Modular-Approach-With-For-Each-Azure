# 🏗️ Terraform Azure Modular Infrastructure (with `for_each`)

A production-ready **Infrastructure as Code (IaC)** project using **Terraform** to deploy a complete **modular Azure environment**.  
Built with **`for_each`** to dynamically create resources like:

- 🌍 **Resource Groups**  
- 🔌 **Virtual Networks, NSGs & NICs**  
- 💻 **Virtual Machines & Bastion**  
- 🗄️ **SQL Server + Databases**  
- ⚖️ **Load Balancers**

Perfect for **DevOps learners** & **Cloud Engineers** who want to master **Terraform + Azure modular design** 🚀.

---

## 🔧 Setup Options

You can use this project in **two ways**:

| Option | Use Case | Docs |
|--------|----------|------|
| 🖥️ **Local Machine** | Run Terraform locally & push state to Azure Blob Storage | [📂 Local Setup](#local-setup) |
| ☁️ **CI/CD Pipeline** | Automate infra with Azure DevOps or GitHub Actions | [🚀 CI/CD Setup](#cicd-setup) |

---

## 📂 Project Structure

```bash
infra/
├── main.tf               # Root module (calls child modules)
├── variables.tf          # Input variable definitions
├── terraform.tfvars      # Values for variables
├── provider.tf           # Provider + remote backend config
├── output.tf             # Exported outputs
└── modules/              # Child modules
    ├── resourceGroup/
    ├── networking/       # VNet, NSG, NIC, PIP, Bastion
    ├── virtual_machine/
    ├── database/         # SQL Server, DB, Firewall
    └── loadBalancer/     # LB, Backend Pool, Probes, Rules
```

---

## ⚙️ Prerequisites

- ✅ [Terraform](https://developer.hashicorp.com/terraform/downloads) v1.6+  
- ✅ [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli) (`az login`)  
- ✅ Azure Storage Account + Container (for remote state)

---

##  Local Setup

```bash
# Step 1: Clone repo
git clone https://github.com/<your-username>/terraform-azure-modular-infra.git
cd terraform-azure-modular-infra/infra

# Step 2: Initialize Terraform
terraform init

# Step 3: Validate & Plan
terraform validate
terraform plan

# Step 4: Apply Infrastructure
terraform apply -auto-approve

# Step 5: Destroy (when not needed)
terraform destroy -auto-approve
```

---

## CI/CD Setup

1. Store backend credentials (Storage Account, Container, Key) in **Azure DevOps/GitHub Secrets**.  
2. Create pipeline stages with Terraform tasks:  
   - `init`  
   - `validate`  
   - `plan`  
   - `apply`  
3. Add **manual approvals** for production deployments.  

---

## 🔐 Security Notes

- ❌ Never push `terraform.tfvars` or credentials to GitHub.  
- ✅ Add sensitive files to `.gitignore`.  

```gitignore
# Terraform state
*.tfstate
*.tfstate.*

# Local cache
.terraform/

# Lock files
*.lock.hcl

# Secrets
terraform.tfvars
```

---

## 📤 Outputs

After deployment you get:  
- Resource Group names & IDs  
- Virtual Network & Subnet IDs  
- NIC IDs & IPs  
- Load Balancer Probe IDs  
- SQL Database IDs  

---

## 📃 License

This project is licensed under **MIT License**.  
Free to use ✨ with attribution.

---

## 👨‍💻 Author

**Ravendra Kumar**  
🔗 [LinkedIn](https://www.linkedin.com/in/ravendra-kumar-21ba29218)  

---

🔥 Terraform + Azure = Scalable, Modular, Production-Ready Infra!
