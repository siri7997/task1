
🔐 Cybersecurity Internship – Task 1
📌 Task: Scan Your Local Network for Open Ports
This repository contains files and documentation for Task 1 of my Cybersecurity Internship, focusing on basic network reconnaissance. The goal is to use Nmap to scan the local network for open ports and identify potential vulnerabilities based on discovered services.

🛠 Tools Used
Nmap (Command Line & Zenmap GUI)

Wireshark (optional) – for packet analysis

🧪 Commands Used
1️⃣ TCP SYN Scan (Human-readable output)
nmap -sS 192.168.68.0/24 -oN nmap_scan_results.txt
2️⃣ XML Output for HTML Conversion (Optional)
nmap -sS 192.168.68.0/24 -oX scan.xml
3️⃣ Save All Formats at Once
nmap -sS 192.168.68.0/24 -oA myscan
4️⃣ Convert XML to HTML (Optional)
xsltproc scan.xml -o scan.html
⚠️ Replace 192.168.68.0/24 with your actual local IP range.

📁 Repository Contents
File Name	Description
nmap_scan_results.txt	Human-readable Nmap scan output
services_and_risks.md	List of open ports and potential vulnerabilities
scan.xml (optional)	XML-format scan output
scan.html (optional)	HTML report converted from XML
README.md	This documentation
📋 Example Nmap Output Summary
PORT     STATE SERVICE
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
⚠️ Risks Identified from Open Ports
Port	Service	Protocol	Description
135	msrpc	TCP	Microsoft RPC – vulnerable to remote RCE
139	netbios-ssn	TCP	NetBIOS – info leakage, file access risks
445	microsoft-ds	TCP	SMB – exploited by ransomware (e.g., WannaCry)
🔍 Risk Analysis
🔓 Port 135 – msrpc
Purpose: Windows RPC services

Risks:

Remote code execution (e.g., Blaster worm)

Network lateral movement

Example Exploit: CVE-2003-0352

🔓 Port 139 – netbios-ssn
Purpose: File/Printer sharing over NetBIOS

Risks:

System information leakage

Unauthorized file access

Man-in-the-middle vulnerabilities

Tools: nbtscan, smbclient, enum

🔓 Port 445 – microsoft-ds
Purpose: SMB for Windows File Sharing

Risks:

Exploited via EternalBlue (e.g., WannaCry)

Enables malware propagation

Attack Vectors: Metasploit, brute-force, SMB relay

✅ Mitigation Recommendations
🔥 Block unused ports using firewall rules

🔒 Restrict access to specific internal IPs

🚫 Disable legacy protocols like SMBv1 and NetBIOS if not needed

🔁 Keep systems regularly patched

🛡 Monitor network logs and use IDS/IPS for unusual port activity

🧠 Key Concepts Covered
Nmap port scanning

TCP SYN scan techniques

Host and service detection

Identifying common vulnerabilities

Basic risk assessment in network environments

📝 Disclaimer: All scans were performed in a safe, isolated lab environment strictly for educational purposes. No external or unauthorized networks were scanned.

