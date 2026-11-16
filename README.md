# 🛡️ Network VAPT Assessment (Metasploitable 2)

## 📌 Project Overview
This repository contains the documentation, evidence, and findings of an End-to-End Network Vulnerability Assessment and Penetration Testing (VAPT) conducted on an authorized lab environment. The target was the intentionally vulnerable **Metasploitable 2** virtual machine, and the assessment was performed from a **Kali Linux** attacker machine.

## 🎯 Scope & Target
*   **Target IP:** `192.168.247.135` (Metasploitable 2)
*   **Attacker IP:** `192.168.247.129` (Kali Linux)
*   **Network Mode:** Host-Only (Isolated Environment)
*   **Testing Type:** Black-Box Network Assessment

## 🛠️ Tools Used
*   **Nmap:** Host discovery, port scanning, and service enumeration.
*   **Nessus Essentials:** Automated vulnerability scanning.
*   **Metasploit Framework:** Manual exploitation and validation of critical vulnerabilities.
*   **Wireshark:** Packet-level traffic analysis and evidence collection.

## 📊 Executive Summary
The assessment identified a total of **69 vulnerabilities** across the target system. The most critical finding was the `vsftpd 2.3.4` Backdoor (CVE-2011-2523), which was successfully exploited to gain root-level access. Other critical findings included SMBv1 (MS17-010 / EternalBlue) and plaintext Telnet services.

### Severity Breakdown (via Nessus)
*   🔴 **Critical:** 8
*   🟠 **High:** 7
*   🟡 **Medium:** 26
*   🟢 **Low:** 8

## 🚀 Methodology & Execution

### 1. Reconnaissance & Scanning
*   Conducted Nmap SYN scan and service version detection (`-sS -sV -p-`).
*   Used NSE vulnerability scripts (`--script vuln`) to identify known flaws.

### 2. Vulnerability Validation
*   Validated the `vsftpd 2.3.4` backdoor using Metasploit (`exploit/unix/ftp/vsftpd_234_backdoor`).
*   Successfully achieved a **Meterpreter root shell**, proving remote code execution.
*   Captured the exploit traffic in Wireshark for packet-level proof.

### 3. Automated Scanning
*   Configured Nessus Essentials and ran a Basic Network Scan.
*   Cross-verified Nmap findings with Nessus reports.

## 📂 Repository Structure
*   `/report/` - Contains the final PDF VAPT Report.
*   `/evidence/` - Contains screenshots of Nmap scans, Metasploit root access, and Nessus dashboard.
*   `/pocs/` - Proof of Concept commands and scripts used during the assessment.

## 🛡️ Remediation Highlights
1.  **vsftpd Backdoor:** Disable the outdated FTP service or upgrade to a secure version (SFTP).
2.  **SMBv1 (MS17-010):** Disable SMBv1 protocol and apply the MS17-010 patch immediately.
3.  **Telnet:** Disable Telnet and replace it with encrypted SSH.

## ⚠️ Disclaimer
This assessment was conducted in a controlled, isolated lab environment (Host-Only) for educational purposes only. No unauthorized systems were targeted or harmed.
