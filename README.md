# SOC Automation Project with AI-Powered Threat Analysis

Automated security operations center (SOC) pipeline that detects, analyzes, and responds to security threats using Splunk SIEM, n8n orchestration, and OpenAI GPT-4.

## 🎯 Project Overview
**Course**: CS-5770 Cybersecurity - Northeastern University  
**Date**: October 2024  
**Author**: Ronan Kongala

This project implements an end-to-end security monitoring pipeline that automatically:
- Detects failed authentication attempts (Event ID 4625)
- Analyzes threats using AI (ChatGPT/OpenAI)
- Maps attacks to MITRE ATT&CK framework
- Sends intelligent notifications via Slack

## 🏗️ Architecture

### Network Configuration
- **Windows 10 VM**: 192.168.116.130 (Event source)
- **Splunk VM**: 192.168.116.128 (SIEM)
- **n8n VM**: 192.168.116.133 (Automation)

### Technology Stack
| Component | Technology | Purpose |
|-----------|------------|---------|
| Event Source | Windows 10 + Sysmon | Generate security events |
| SIEM | Splunk Enterprise | Log aggregation and alerting |
| Orchestration | n8n (Docker) | Workflow automation |
| Analysis | OpenAI GPT-4 | Threat intelligence |
| Notification | Slack | Security alerts |

## 📸 Implementation Flow (Event Journey)

### Step 1: Windows Infrastructure Setup
![Windows IP Configuration](./screenshots/10-windows-ip-configuration.png.png)
*Windows VM network configuration (192.168.116.130)*

![Windows Security Services](./screenshots/06-windows-security-services.png.png)
*Windows security services running and monitoring*

### Step 2: Event Generation & Collection
![Failed Login Generation](./screenshots/09-failed-login-generation.png.png)
*PowerShell script generating test failed authentication events*

![Event Detection](./screenshots/07-windows-event-viewer-4625.png.png)
*Windows Event Viewer showing 27 captured failed login attempts (Event ID 4625)*

![Splunk Forwarder Status](./screenshots/08-splunk-forwarder-status.png.png)
*Splunk Universal Forwarder running on port 9997*

### Step 3: SIEM Processing
![Splunk Login](./screenshots/11-splunk-login-page.png.png)
*Splunk Enterprise login interface*

![Splunk Dashboard](./screenshots/12-splunk-dashboard-main.png.webp)
*Splunk main dashboard showing Search & Reporting capabilities*

![Splunk Search](./screenshots/14-splunk-search-failed-logins.png.png)
*Splunk detecting 5 failed authentication events with Event ID 4625*

![Splunk Alert Configuration](./screenshots/15-splunk-alert-configuration.png.png)
*Configured alert "test-brute-force" set to trigger on failed logins*

### Step 4: Automation & AI Analysis
![n8n Execution Success](./screenshots/25-n8n-execution-success.png.png)
*n8n workflow showing 5 successful executions with processing times*

### Step 5: Alert Notification
![Slack Alert Message](./screenshots/32-slack-alert-message.png.png)
*AI-analyzed security alert delivered to Slack #alerts channel*

![Slack Alert Details](./screenshots/33-slack-alert-details.png.png)
*Detailed threat analysis with MITRE ATT&CK mapping and response recommendations*

### Step 6: Troubleshooting
![Disk Space Error](./screenshots/39-error-disk-space.png.png)
*Splunk disk space issue encountered and resolved during implementation*

## 🔧 Challenges & Solutions
| Challenge | Solution |
|-----------|----------|
| Splunk disk space (5GB requirement) | Modified config to 2GB minimum: `minFreeSpace = 2000` |
| VM IP address changes (129→133) | Updated webhook URLs and documented static IP configuration |
| n8n workflow persistence | Implemented Docker volumes for data retention |
| Cross-VM communication | Consolidated services and verified network connectivity |

## 📊 Results & Metrics
- **Detection Rate**: 100% of test events captured
- **Detection Speed**: < 60 seconds from event to alert
- **Processing Time**: Average 8.95 seconds (range: 35ms - 8.95s)
- **Automation Success Rate**: 5/5 executions successful
- **AI Analysis Accuracy**: Correctly identified severity and provided context

### Key Achievements
✅ Full pipeline automation from detection to notification  
✅ AI correctly assessed threats and mapped to MITRE framework  
✅ Zero false positives during testing  
✅ Successfully integrated 6 different technologies  

## 🛠️ Setup Requirements

### Hardware Requirements
- Host machine: 32GB RAM minimum
- Storage: 150GB free space
- Processor: 8+ cores recommended

### Software Requirements
- VMware Workstation Pro
- Windows 10 ISO
- Ubuntu Server 24.04 ISO
- Docker & Docker Compose
- Splunk Enterprise License

### API Keys Required
- OpenAI API key
- Slack Bot Token
- Slack Workspace access

## 💡 Key Learnings
1. **SIEM Management**: Disk space management is critical for Splunk operation
2. **Network Architecture**: Static IP assignment prevents workflow disruption
3. **Container Persistence**: Docker volumes essential for maintaining configurations
4. **API Integration**: Webhook reliability depends on network stability
5. **Troubleshooting**: Systematic approach to debugging cross-platform integrations

## 🚀 Future Improvements
- [ ] Add VirusTotal API for malware hash analysis
- [ ] Implement automated containment actions
- [ ] Expand detection rules (PowerShell, privilege escalation)
- [ ] Create Splunk dashboard for SOC metrics
- [ ] Add email notifications alongside Slack
- [ ] Implement TheHive for case management

## 🎓 Skills Demonstrated
- **SIEM Deployment**: Splunk Enterprise configuration and management
- **Security Automation**: n8n workflow orchestration
- **API Integration**: OpenAI, Slack, webhook implementations
- **Container Management**: Docker deployment and troubleshooting
- **Network Configuration**: Static IP, cross-VM communication
- **Log Analysis**: SPL queries, event correlation
- **Incident Response**: Automated triage and notification
- **Problem Solving**: Systematic debugging and documentation

## 📧 Contact
**Ronan Kongala**  
MS Cybersecurity @ Northeastern University  
Email: ronanlucky@gmail.com  
LinkedIn: [linkedin.com/in/ronan-kongala](https://www.linkedin.com/in/ronan-kongala-99068a240/)

---
*This project was completed as part of CS-5770 coursework and demonstrates practical implementation of enterprise SOC capabilities.*
