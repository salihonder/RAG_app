# Core Azure Services and How to Use Them

---

## 1. Identity & Access – Azure Active Directory (Entra ID)

### **What it is**
Cloud identity and access management for users, apps, and devices.

### **What you do with it**
- Create users & groups  
- Set up Single Sign-On (SSO) for apps  
- Configure Multi-Factor Authentication (MFA)  
- Manage role-based access (RBAC) for Azure resources  

### **How (high level)**
- **Portal:** Azure Portal → *Microsoft Entra ID*  
- **Create a user:** Users → *New user*  
- **Create a group:** Groups → *New group*  
- **Assign a role to a user on a resource:**  
  Resource → *Access control (IAM)* → *Add role assignment*

---

## 2. Compute – Azure Virtual Machines (VMs)

### **What it is**
Infrastructure-as-a-Service virtual servers (Windows/Linux).

### **What you do with it**
- Lift-and-shift on-prem apps  
- Run custom workloads (DBs, tools, agents)  
- Create test and dev environments  

### **How**
- **Portal:** Virtual Machines → *Create*  
- Choose image (Ubuntu, Windows, etc.)  
- Pick size (CPU/RAM)  
- Configure disk, VNet, NSG (firewall)  

### **Access**
- **Linux:** SSH → `ssh user@public-ip`  
- **Windows:** RDP → `mstsc`  

---

## 3. Managed Web Apps – App Service

### **What it is**
Platform-as-a-Service for running web apps and APIs without managing VMs.

### **What you do with it**
- Deploy Python, Node, .NET, Java web apps  
- Host REST APIs  
- Set up staging slots and CI/CD  

### **How**
- **Portal:** App Services → *Create*  
- Choose runtime (Node 20, .NET 8, Python 3.11…)  

### **Deploy**
- Local Git  
- GitHub Actions  
- Azure DevOps  
- Zip deploy / FTP  

### **Configure**
- Settings → *Configuration* (environment variables)  
- Scale out using App Service Plan scaling  

---

## 4. Serverless – Azure Functions

### **What it is**
Serverless compute that runs code on triggers (HTTP, timers, queues, etc.).

### **What you do with it**
- Build lightweight APIs  
- Process queue messages  
- Event-driven tasks (CRON jobs, webhooks)  

### **How**
- **Portal:** Function Apps → *Create*  
- Choose runtime stack (Node, Python, .NET, etc.)  

### **Create functions with triggers**
- **HTTP trigger:** simple API endpoint  
- **Timer trigger:** scheduled job  
- **Queue trigger:** process messages from Storage queues / Service Bus  

### **Local development**
- Use Azure Functions Core Tools (`func CLI`) + VS Code  
- Publish to Azure  

---

## 5. Containers – Azure Container Instances / Azure Kubernetes Service (AKS)

---

### **5.1 Azure Container Instances (ACI)**

#### **What it is**
Run single containers without managing servers.

#### **What you do**
- Quick containerized jobs  
- Simple APIs or background workers  

#### **How**
- **Portal:** Container instances → *Create*  
- Provide image from ACR or Docker Hub  
- Set CPU/RAM, env vars, ports  

---

### **5.2 Azure Kubernetes Service (AKS)**

#### **What it is**
Managed Kubernetes cluster.

#### **What you do**
- Run microservices  
- Deploy scalable container workloads  
- Use ingress, autoscaling, etc.  

#### **How**
- **Portal:** Kubernetes services → *Create*  
- Deploy apps using:
  - `kubectl`
  - YAML manifests  
  - Helm charts  
- Integrate with:
  - ACR for private images  
  - Azure CNI for networking  

---

## 6. Storage – Azure Storage (Blob, Files, Queues, Tables)

### **What it is**
Core storage platform.

### **Main services**
- **Blob Storage:** Object storage (files, images, backups)  
- **File Shares:** SMB file shares  
- **Queues:** Simple message queues  
- **Tables:** NoSQL key/attribute store  

### **What you do**
- Store files, logs, backups  
- Host static websites  
- Use queues for async processing  

### **How**
- **Portal:** Storage accounts → *Create*  

Inside a storage account:
- *Containers* → create blob containers  
- *File shares* → mount SMB  
- *Queues* → send/receive messages via SDK  

Use SDKs (`azure-storage-blob`, etc.) in Python/Node/.NET.

---

## 7. Databases – Azure SQL Database & Cosmos DB

---

### **7.1 Azure SQL Database**

#### **What it is**
Managed SQL Server in the cloud.

#### **What you do**
- Run transactional relational databases  
- Use for web apps, business apps  

#### **How**
- Portal: SQL databases → *Create*  
- Define:
  - Server  
  - Pricing tier (DTU/vCore)  
- Connect with connection string  
- Manage schema with:
  - SSMS  
  - Azure Data Studio  
  - EF migrations  

---

### **7.2 Azure Cosmos DB**

#### **What it is**
Distributed NoSQL DB with multiple APIs (SQL, Mongo, Cassandra, Gremlin, Table).

#### **What you do**
- Global-scale apps  
- JSON document stores  
- Low-latency reads in multiple regions  

#### **How**
- Portal: Azure Cosmos DB → *Create*  
- Choose API (usually SQL)  
- Use SDKs to:
  - upsert  
  - query  
- Enable multi-region replication  

---

## 8. Networking – VNet, Subnets, NSG, Application Gateway

### **Core pieces**
- **Virtual Network (VNet):** Private network  
- **Subnets:** Network segments  
- **NSGs:** Firewall rules  
- **Application Gateway:** L7 load balancer, WAF  
- **Azure Front Door:** Global edge + WAF + CDN  

### **What you do**
- Isolate workloads  
- Control inbound/outbound traffic  
- Securely publish apps  

### **How**
- VNet/Subnets: Virtual networks → *Create*  
- Attach VMs, AKS to subnets  
- NSG: create, then associate with subnet or NIC  
- App Gateway: Create → attach to subnet → configure listeners & backend pools  

---

## 9. Observability – Azure Monitor, Application Insights, Log Analytics

### **What it is**
- **Azure Monitor:** Full monitoring framework  
- **Application Insights:** App performance & telemetry  
- **Log Analytics:** Query logs with KQL  

### **What you do**
- View metrics (CPU, requests, latency)  
- Collect logs & traces  
- Build dashboards and alerts  

### **How**
- Enable Application Insights when creating App Service / Functions  
- Logs: Log Analytics Workspace → *Logs*  
- Alerts: Alerts → *New alert rule*  

---

## 10. Messaging & Integration – Service Bus, Event Grid, Event Hubs

### **Service Bus**
- **What:** Enterprise messaging (queues, topics)  
- **Use:** Decoupled microservices, reliable messaging  

### **Event Grid**
- **What:** Event routing  
- **Use:** Trigger Functions/webhooks on resource events  

### **Event Hubs**
- **What:** Big data ingestion  
- **Use:** Streaming telemetry, logs, analytics pipelines  

### **How**
- Create Namespace (Service Bus / Event Hubs)  
- Create queues/topics/hubs  
- Use SDKs to send/receive messages  

---

## 11. AI & Cognitive – Azure OpenAI, Cognitive Services

### **What it is**
- **Azure OpenAI:** GPT-style models  
- **Cognitive Services:** Vision, Speech, Language APIs  

### **What you do**
- Build chatbots and copilots  
- Text analytics, translation, image analysis  
- RAG apps  

### **How**
- Create an Azure OpenAI resource  
- Deploy a model (`gpt-4o`, `gpt-4o-mini`)  
- Call via REST or SDK  

---

## 12. Security & Governance – Key Vault, Defender, Policy

### **Key Vault**
- Store secrets, keys, certificates  
- **How:**  
  Key Vault → Secrets → *Generate/Import*  
  Use Managed Identity to access secrets  

### **Azure Policy**
- Enforce rules (no public IPs, location restrictions)  
- Assign at Subscription or Resource Group  

### **Defender for Cloud**
- Security posture, vulnerability scanning, recommendations  

---

## 13. DevOps & Automation – Azure DevOps, GitHub Actions, Automation

### **Azure DevOps**
- Repos  
- Pipelines  
- Boards  
- Artifacts  
- Build & deploy Azure resources  

### **GitHub Actions**
- CI/CD with Azure login  
- Deploy to App Service, Functions, AKS, etc.  

### **Azure Automation / Logic Apps**
- **Runbooks** (PowerShell/Python automation)  
- **Logic Apps** for low-code workflows  

---

# Practical Learning Path: “How to Learn Azure in Order”

### **Identity & IAM**
- Azure AD / Entra ID  
- RBAC  

### **Compute & Web**
- Virtual Machines  
- App Service  
- Azure Functions  

### **Data**
- Blob Storage  
- Azure SQL  
- Cosmos DB  

### **Networking**
- VNet, Subnets, NSG  
- Application Gateway / Front Door  

### **Observability**
- Azure Monitor  
- Application Insights  
- Log Analytics  

### **Messaging**
- Service Bus  
- Event Grid  

### **Security**
- Key Vault  
- Defender  
- Policies  

### **AI**
- Azure OpenAI  
- RAG apps on Azure  

---
