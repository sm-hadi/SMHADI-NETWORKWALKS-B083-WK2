# W2-PM-FINAL – SYED MUHAMMAD HADI – Batch B083-Networkwalks

### Footprinting, Reconnaissance & Network Scanning Report

---

## 📋 Overview

This repository contains the Week 2 practical report for the Cybersecurity Program at Networkwalks[cite: 6]. The report covers the following activities:
1. **Footprinting & Reconnaissance** against `networkwalks.com` using six Kali Linux tools[cite: 6].
2. **Network Scanning** of a local subnet using Zenmap (Nmap GUI)[cite: 6].
3. **Google Hacking Database (GHDB) Footprinting** using advanced Google dork queries to discover exposed webcams, directory listings, and sensitive files.

All activities were performed only on systems where written permission was obtained or on systems owned by the author, strictly for educational and research purposes[cite: 6].

---

## 🛠️ Tools Used

| Tool | Purpose |
| :--- | :--- |
| **Kali Linux & Windows** | Operating systems used for reconnaissance activities[cite: 6] |
| **WHOIS** | Find domain registration details (owner, dates, name servers)[cite: 6] |
| **WhatWeb** | Fingerprint web technologies (server, CMS, plugins, IP)[cite: 6] |
| **Nslookup** | Resolve the domain name to its IP address using DNS[cite: 6] |
| **Curl -I** | Read the HTTP response headers of the website[cite: 6] |
| **Wafw00f** | Detect whether a Web Application Firewall protects the site[cite: 6] |
| **DNSRecon** | Enumerate all DNS records (NS, MX, SPF, TXT, SRV)[cite: 6] |
| **Zenmap (Nmap GUI)** | Scan the local subnet to find live hosts, IPs and MAC addresses[cite: 6] |
| **Windows CMD** | Local IP and MAC address identification[cite: 6] |
| **Google Dorks (GHDB)** | Discover publicly exposed files, cameras, and directories |

---

## 🔍 Key Findings

### 4.1 Footprinting (networkwalks.com)
* **WHOIS:** Identified domain registration and name servers[cite: 6].
* **WhatWeb:** Detected WordPress 7.0.4 and WP Download Manager 3.3.58[cite: 6].
* **Nslookup:** Resolved domain to IP `192.232.216.135`[cite: 6].
* **Curl -I:** Exposed HTTP headers and WordPress REST API endpoint `/wp-json/`[cite: 6].
* **Wafw00f:** Identified ModSecurity (SpiderLabs) WAF[cite: 6].
* **DNSRecon:** Enumerated NS, MX, SPF/TXT, and SRV records[cite: 6].

### 4.2 Network Scanning (Zenmap)
* **Local IP:** `192.168.1.6`[cite: 6]
* **LAN Subnet:** `192.168.1.0/24`[cite: 6]
* **Live Hosts Discovered:** `5` hosts live[cite: 6]
* **Scan Command / Profile:** Quick scan (`nmap -T4 -F 192.168.1.0/24`)[cite: 6]
* **Live Host Details:**
  * `192.168.1.1` | MAC: `68:D1:BA:81:A3:68`[cite: 6]
  * `192.168.1.2` | MAC: `2E:F3:D2:C4:5C:4B`[cite: 6]
  * `192.168.1.6` | (Local PC)[cite: 6]
  * `192.168.1.7` | MAC: `7E:E2:FF:4E:28:65`[cite: 6]
  * `192.168.1.9` | MAC: `A2:E5:C2:AB:C5:12`[cite: 6]

---

### 4.3 Google Hacking Database (GHDB) Footprinting
Advanced Google dork queries were used to discover exposed directory listings, publicly accessible webcams, and sensitive files.

#### 4.3.1 Public Camera Details (Google Dorks)

| # | Google Dork Query | Target URL / Result Reference |
| :-: | :--- | :--- |
| **1** | `intitle:"webcamXP" inurl:8080` | http://109.233.191.130 |
| **2** | `intitle:"Webcam" inurl:WebCam.htm` | https://www.lmc.edu/webcam.htm |
| **3** | `intitle:"Index of /webcam/"` | https://ns.ph.liv.ac.uk/webcam/ |
| **4** | `inurl:webcam site:skylinewebcams.com inurl:roma` | https://www.skylinewebcams.com/webcam/italia/lazio/roma/piazza-di-spagna.html |
| **5** | `inurl:/multi.html intitle:webcam` | http://68.115.218.130:32479/home.html |
| **6** | `intitle:"webcamxp" "Flash JPEG Stream"` | http://109.233.191.130:8080/ |
| **7** | `inurl:/ViewerFrame? intitle:"Network Camera NetworkCamera"` | http://80.152.138.183/ViewerFrame?Mode=Motion&Language=0 |
| **8** | `intitle:"Biromsoft WebCam" -4.0 -serial` | https://www.stonecircle.us/WebCam/cam.html |
| **9** | `"powered by webcamXP" "Pro\|Broadcast"` | *(query only)* |
| **10** | `inurl:"live/cam.html"` | http://www.insecam.org/en/bytype/webcamxp/ |

#### 4.3.2 Specific PDF Documents (Google Dorks)

| # | Google Dork Query | Target URL / Result Reference |
| :-: | :--- | :--- |
| **1** | `intitle:index.of "parent directory" mathematics pdf` | https://www.unm.edu/~megrad/Math/ |
| **2** | `intitle:index.of "parent directory" calculus pdf` | https://www.aetkin.com/files/Math%20150%20Calculus%20I/Advanced%20Calculus%20Textbook/ |
| **3** | `intitle:index.of "parent directory" linear algebra pdf` | https://math.mit.edu/~gs/linearalgebra/ila6/ |
| **4** | `intitle:index.of "parent directory" differential equation pdf` | https://www.aerostudents.com/courses/differential-equations/ |
| **5** | `intitle:index.of "parent directory" discrete mathematics pdf` | https://discrete.openmathbooks.org/pdfs/ |
| **6** | `intitle:index.of "parent directory" probability and statistics pdf` | https://www.aerostudents.com/courses/probability-and-statistics/ |
| **7** | `intitle:index.of "parent directory" geometry pdf` | https://www.cs.tufts.edu/research/geometry/pdf/ |
| **8** | `intitle:index.of "parent directory" trigonometry pdf` | http://www.wallace.ccfaculty.org/book/ |
| **9** | `intitle:index.of "parent directory" hc verma pdf` | https://discrete.openmathbooks.org/pdfs/ |
| **10** | `intitle:index.of "parent directory" c++ pdf` | https://ce.cet.ac.in/downloads/Study%20Material/Computer%20Programming/ |

#### 4.3.3 Key Observations
* Exposed webcams are often accessible via default ports (e.g., 8080) and weak authentication.
* Directory listings (`intitle:index.of "parent directory"`) expose files that were not intended to be publicly browsable.
* Google dorks can reveal sensitive documents, login panels, and device interfaces without any exploitation.
* These findings highlight the importance of proper server configuration, access controls, and `robots.txt` / `noindex` directives to prevent unintended exposure.

#### 4.3.4 Risk Summary (GHDB)

| # | Risk / Finding | Potential Impact | Risk Level |
| :-: | :--- | :--- | :--- |
| **1** | Publicly accessible webcams | Privacy breach, unauthorized surveillance | High |
| **2** | Exposed directory listings | Sensitive files may be downloaded or indexed | Medium |
| **3** | PDF documents publicly indexed | Information leakage, copyright / academic integrity issues | Low |

---

## ⚠️ Risk Analysis Summary

| # | Risk / Finding | Risk Level |
| :-: | :--- | :--- |
| **1** | Web technology information exposed (WordPress, plugins) | Medium[cite: 6] |
| **2** | Server IP address identifiable | Low[cite: 6] |
| **3** | HTTP technical information exposed (`/wp-json/`) | Low[cite: 6] |
| **4** | WAF technology identifiable (ModSecurity) | Low[cite: 6] |
| **5** | DNS infrastructure information exposed | Medium[cite: 6] |
| **6** | Live hosts visible on local network (5 active hosts) | Medium[cite: 5, 6] |
| **7** | Publicly accessible webcams discovered | High |
| **8** | Exposed directory listings | Medium |
| **9** | Publicly indexed PDF documents | Low |

*Note: These are observations from information gathering, not confirmed vulnerabilities. No exploitation was performed[cite: 6].*

---

## 📸 Evidence Collected

All screenshots are included in Section 8 of the full report[cite: 6]:
* WHOIS Lookup[cite: 6]
* WhatWeb Fingerprinting[cite: 6]
* Curl HTTP Headers[cite: 6]
* Wafw00f WAF Detection[cite: 6]
* DNSRecon Enumeration[cite: 6]
* Zenmap Network Scan (`192.168.1.0/24`)[cite: 5, 6]
* Local IP Configuration (`ipconfig`)[cite: 5, 6]
* Saved Network Topology Graphic (PDF)[cite: 5, 6]
* Google Dork Results (Webcams)
* Google Dork Results (PDF Documents)

---

**Author / Pentester:** **SYED MUHAMMAD HADI**[cite: 6]  
**Batch:** **B083-Networkwalks**[cite: 6]
