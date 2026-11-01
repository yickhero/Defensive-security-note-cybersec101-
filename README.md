# Defensive-security-note-cybersec101-
Here are my notes after completing tryhackme defensive security module
# SOC, Digital Forensics & Incident Response Notes

## Security Operations Center (SOC) Fundamentals

The main focus of a SOC team is to maintain intact Detection and Response capabilities across an organization's infrastructure.

### Core Objectives

* **Detection:**
* *Vulnerabilities:* Identifying weaknesses that attackers could exploit to escalate privileges.
* *Unauthorized Activity:* Detecting anomalous behavior, such as compromised credentials being used for unauthorized access.
* *Intrusions:* Identifying unauthorized access to internal systems and networks.


* **Response:** Supporting incident response efforts, minimizing impact, and performing root cause analysis of security incidents.

### The Three Pillars of a SOC

#### 1. People

* **SOC Analyst (Level 1):** First responders to alerts. They perform basic triage to determine if a detection is harmful and escalate legitimate threats through proper channels.
* **SOC Analyst (Level 2):** Perform deeper investigations, correlating data from multiple sources to conduct comprehensive analysis on escalated alerts.
* **SOC Analyst (Level 3):** Experienced professionals who proactively hunt for threat indicators and lead incident response activities (containment, eradication, recovery) for critical severity incidents.
* **Security Engineer:** Responsible for deploying, configuring, and maintaining security solutions (SIEM, EDR, Firewalls) to ensure smooth operation.
* **Detection Engineer:** Creates the logic and security rules behind security solutions to detect malicious activities.
* **SOC Manager:** Manages SOC processes, supports the team, and updates the organization's CISO on the current security posture and ongoing efforts.

#### 2. Process

* **Triage (The 5 W's):** The initial response to an alert.
* *What:* A malicious file was detected.
* *When:* Time of detection (e.g., 13:20 on June 5, 2024).
* *Where:* The host machine or directory (e.g., "GEORGE PC").
* *Who:* The user account involved (e.g., User: George).
* *Why:* The root cause (e.g., User downloaded pirated software).


* **Reporting:** Malicious alerts are escalated as tickets to higher-level analysts. Reports must include the 5 W's, a thorough analysis, and screenshot evidence.
* **Incident Response & Forensics:** Critical alerts trigger high-level IR teams to contain the threat and perform digital forensics to determine the root cause by analyzing system artifacts.

#### 3. Technology

* **SIEM (Security Information and Event Management):** A centralized solution that collects and correlates logs from various network devices. Modern SIEMs utilize user behavior analytics, threat intelligence, and machine learning to alert analysts of suspicious activity.
* **EDR (Endpoint Detection and Response):** Provides real-time and historical visibility into device activities at the endpoint level. EDR possesses extensive detection capabilities and can execute automated responses.
* **Firewall:** Operates at the network level, acting as a barrier between internal and external networks. Monitors and filters unauthorized traffic based on deployed detection rules.

---

## Digital Forensics Fundamentals

Digital forensics is the application of scientific methods to investigate and solve cybercrimes.

### Four Phases of Digital Forensics

1. **Collection:** Identifying and acquiring data from all relevant devices.
2. **Examination:** Filtering the massive volume of collected data to extract the specific data of interest.
3. **Analysis:** Correlating extracted data with multiple pieces of evidence to draw factual conclusions.
4. **Reporting:** Documenting the investigation's methodology, detailed findings, and security recommendations.

### Types of Digital Forensics

* **Computer Forensics:** Investigating traditional computing devices.
* **Mobile Forensics:** Extracting evidence from mobile devices (call records, SMS, GPS locations).
* **Network Forensics:** Analyzing network traffic logs to investigate widespread intrusions.
* **Database Forensics:** Investigating unauthorized access, data modification, or exfiltration within databases.
* **Cloud Forensics:** Investigating data stored on cloud infrastructure (often complex due to limited physical evidence).
* **Email Forensics:** Analyzing emails to investigate phishing, fraud, or malware campaigns.

### Chain of Custody & Acquisition

* **Chain of Custody:** A formal document detailing the lifecycle of evidence to maintain legal integrity. It includes:
1. Description of evidence (name, type).
2. Name of the collecting individual.
3. Date and time of collection.
4. Storage location.
5. Access logs (who accessed it and when).


* **Write Blocker:** A hardware or software tool that allows investigators to collect data from a drive while strictly preventing any data alteration on the source disk.

### Forensic Images

* **Memory Image (Volatile):** Contains data actively running in RAM (open files, running processes, active network connections). Data is lost if the system powers off. *Must be prioritized and captured first.*
* **Disk Image (Non-Volatile):** Contains all data on the storage device (HDD/SSD), including media, documents, and browsing history. Data survives reboots.

### Forensic Tools

| Tool | Primary Function | Description |
| --- | --- | --- |
| **FTK Imager** | Disk Acquisition | Takes forensic disk images in various formats and allows for preliminary analysis. |
| **Autopsy** | Disk Analysis | Open-source platform for extensive analysis, keyword searching, and deleted file recovery. |
| **DumpIt** | Memory Acquisition | Command-line utility to rapidly capture a Windows memory image. |
| **Volatility** | Memory Analysis | Open-source tool with plugins to analyze specific artifacts within memory captures. |
| **Pdfinfo** | File Analysis | Displays PDF metadata (title, author, creation date). |
| **ExifTool** | File Analysis | Reads and writes metadata in various files, commonly used for JPEG EXIF data. |

---

## Incident Response (IR)

### Common Incident Types

* Malware infections
* Security breaches
* Data leaks
* Insider attacks
* Denial of Service (DoS): Attackers flood a system with false requests to exhaust resources and deny access to legitimate users.

### Incident Response Frameworks

Two major frameworks guide the incident response lifecycle:

**SANS Framework (PICERL):**

1. **Preparation:** Building resources and policies to handle incidents.
2. **Identification:** Detecting anomalous behavior indicating an incident.
3. **Containment:** Isolating the threat to minimize impact.
4. **Eradication:** Completely removing the threat from the environment.
5. **Recovery:** Restoring affected systems from backups and returning to normal operations.
6. **Lessons Learned:** Post-incident review to improve future responses.

**NIST Framework:**

1. Preparation
2. Detection and Analysis
3. Containment, Eradication, and Recovery
4. Post-Incident Activity

### IR Documentation

* **Incident Response Plan:** The formal, high-level document outlining roles, responsibilities, methodologies, communication plans, and escalation paths.
* **Playbooks:** High-level workflows for specific incidents (e.g., Phishing Playbook: Notify stakeholders -> Analyze headers/body -> Analyze attachments -> Determine user interaction -> Isolate systems -> Block sender).
* **Runbooks:** Granular, step-by-step technical instructions for executing the steps defined in a playbook.

---

## Log Fundamentals

Logs are the foundation of security monitoring, providing a historical trail of system and network activities.

### Purpose of Logs

* **Security Events Monitoring:** Detecting anomalous behavior in real-time.
* **Investigation & Forensics:** Providing traces of activity to perform root cause analysis.
* **Troubleshooting:** Diagnosing errors and fixing system or application issues.
* **Performance Monitoring:** Gaining insights into application efficiency.
* **Auditing & Compliance:** Establishing a verifiable trail of activities to meet regulatory standards.

### Types of Logs

* **System Logs:** OS-level activities (startup/shutdown, driver loading, hardware events).
* **Security Logs:** Security-related activities (authentication, authorization, policy changes).
* **Application Logs:** Software-specific events (user interactions, application errors/updates).
* **Audit Logs:** Detailed records of system changes and data access for compliance.
* **Network Logs:** Traffic flow information (incoming/outgoing traffic, firewall blocks).
* **Access Logs:** Records of access to resources (web server, database, or API access).

### Windows Event Logs

Windows OS stores activities in specific log categories, viewable via the **Event Viewer** GUI utility.

**Key Windows Log Files:**

* **Application:** Logs software errors, warnings, and compatibility issues.
* **System:** Logs OS operations, driver issues, and startup/shutdown data.
* **Security:** The most critical log for SOC analysts, recording all authentication and policy changes.

**Event Log Fields:** Description, Log Name, Logged (Timestamp), and Event ID.

**Crucial Windows Security Event IDs:**

| Event ID | Description |
| --- | --- |
| **4624** | A user account successfully logged in. |
| **4625** | A user account failed to log in. |
| **4634** | A user account successfully logged off. |
| **4720** | A user account was created. |
| **4722** | A user account was enabled. |
| **4724** | An attempt was made to reset an account's password. |
| **4725** | A user account was disabled. |
| **4726** | A user account was deleted. |

### Command Line Log Analysis Tools (Linux)

* **grep:** Searches for specific strings or patterns inside a log file.
* *Example:* `grep "192.168.1.1" access.log` (Extracts all lines containing that IP).


* **less:** Allows viewing of large log files one page at a time without overwhelming the terminal.
* *Example:* `less access.log`
* *Navigation:* `Spacebar` (next page), `b` (previous page), `/pattern` (search forward for a string), `n` (next match), `N` (previous match).