# 🛡️ Splunk SIEM Home Lab

## 📌 Overview
This project demonstrates how I built a **home SIEM lab** using Splunk Enterprise Free.  
The goal was to ingest logs from Windows and Linux systems, create detections for suspicious activity, and build dashboards/alerts to monitor security events.

---

## ⚙️ Tools & Technologies
- Splunk Enterprise Free (SIEM)
- Splunk Universal Forwarder
- Windows Event Logs (Security Events)
- Linux syslog (`/var/log/auth.log`)
- Virtual Machines (local or cloud)

---

## 🚀 Setup Process

### 1. Splunk Installation
- Installed Splunk Enterprise Free on a test VM.  
- Accessed the web interface at `http://<server-ip>:8000`.  

📸 *Screenshot: Splunk login page*

---

### 2. Log Collection
- Installed **Splunk Universal Forwarder** on Windows VM to send Security Event Logs.  
- Configured a Linux VM to forward SSH authentication logs from `/var/log/auth.log`.  

📸 *Screenshot: Logs visible in Splunk search screen*

---

### 3. Security Detections

**Failed Windows Login Attempts**
```spl
index=wineventlog sourcetype=WinEventLog:Security EventCode=4625
| stats count by Account_Name, ComputerName, _time
