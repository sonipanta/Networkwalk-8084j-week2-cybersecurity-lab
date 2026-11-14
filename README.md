# Networkwalk-8084j-week2-cybersecurity-lab
# Penetration Testing Report
## Footprinting & Network Scanning Phases

**Program:** W2-PM-FINAL  
**Domain:** Cybersecurity  
**Organization:** NetworkWalk  
**Week:** 2

---

## Table of Contents

1. [Liability Disclaimer](#1-liability-disclaimer)
2. [Introduction](#2-introduction)
3. [Tools Used](#3-tools-used)
4. [Activities Performed](#4-activities-performed)
   - [4.1 Footprinting Using Kali Linux Tools](#41-footprinting-using-kali-linux-tools)
   - [4.2 Network Scanning with Zenmap](#42-network-scanning-with-zenmap)
5. [Risk Analysis](#5-risk-analysis)
6. [Recommendations](#6-recommendations)
7. [Conclusion](#7-conclusion)
8. [Evidence Collected](#8-evidence-collected)

---

## 1. Liability Disclaimer

I performed these activities only on systems and devices for which I had secured written permission or that I personally owned. All materials are intended for educational and research purposes only.

The instructor, authors, and NetworkWalk are not responsible for any misuse of the knowledge presented in this report. Every action taken using these techniques is the responsibility of the individual. Unauthorized access may result in criminal charges, financial penalties, and other legal consequences.

---

## 2. Introduction

During the second week of my internship at NetworkWalk, I focused on learning practical cybersecurity concepts, particularly footprinting and network scanning.

I completed the following modules:

- **Module 1:** Footprinting Using Kali Linux Tools
- **Module 5:** Zenmap-Based Network Scanning

These modules helped me understand how cybersecurity professionals gather information about target systems, identify website technologies, and discover devices connected to a network.

---

## 3. Tools Used

### Module 1: Footprinting Using Kali Linux Tools

| Tool | Purpose |
|---|---|
| WHOIS | Gather domain registration information, registrar details, and name servers. |
| WhatWeb | Identify website technologies and frameworks. |
| Nslookup | Retrieve DNS information, including IP addresses and domain records. |
| cURL | Inspect HTTP response headers. |
| DNSRecon | Perform DNS reconnaissance and information gathering. |
| WAFW00F | Identify Web Application Firewalls (WAFs). |

### Module 5: Zenmap-Based Network Scanning

| Tool | Purpose |
|---|---|
| Zenmap | Graphical interface for Nmap used to perform network scans and visualize results. |
| Nmap | Discover live hosts, identify devices, and perform network scanning. |

---

## 4. Activities Performed

### 4.1 Footprinting Using Kali Linux Tools

For the first activity, I performed reconnaissance on the **networkwalks.com** domain using six Kali Linux tools: WHOIS, WhatWeb, Nslookup, cURL, WAFW00F, and DNSRecon.

Each tool was used to gather a different type of publicly available information about the target domain.

**1. WHOIS**

I used WHOIS to obtain domain registration information. The results showed:

- Registrar: GoDaddy.com, LLC
- Creation Date: November 6, 2019
- Name Servers:
  - NS6135.HOSTGATOR.COM
  - NS6136.HOSTGATOR.COM
  - NS29.DOMAINCONTROL.COM
  - NS30.DOMAINCONTROL.COM
- Registrant information was protected through a privacy service.

**2. WhatWeb**

I used WhatWeb to identify the technologies used by the website.

The results identified:

- WordPress 7.1.4
- WP Download Manager 3.3.76
- jQuery 3.7.1
- Apache
- Bootstrap 7.1.4

It also revealed additional website information, including the website title, email address, and IP address `192.232.216.135`.

**3. Nslookup**

I used Nslookup to perform DNS lookup and resolve the domain name to its associated IP address.

**4. curl**

I used curl with the `-I` option to inspect HTTP response headers.

The result showed an HTTP **301 Moved Permanently** status, indicating that HTTP requests were redirected to the HTTPS version of the website.

The response headers also revealed information about the Apache web server, WordPress-related headers, and the destination URL.

**5. WAFW00F**

I used WAFW00F to determine whether a Web Application Firewall was protecting the website.

The result identified **ModSecurity (SpiderLabs)** as the Web Application Firewall.

**6. dnsrecon**

I used DNSRecon to perform DNS enumeration and gather DNS-related information.

The captured results displayed SOA and NS records associated with the domain, including name server information and an IP address associated with the SOA record.

**Learning Outcome:**

Through these activities, I gained practical experience in domain information gathering, website technology identification, DNS enumeration, HTTP header inspection, and firewall detection.

---

### 4.2 Network Scanning with Zenmap

For the second activity, I used **Zenmap**, the graphical user interface of Nmap, to perform network discovery on my local network.

First, I used the Windows `ipconfig` command to identify my laptop's local IP address and subnet.

My network details were:

| Network Information | Value |
|---|---|
| Laptop IP Address | `192.168.18.202` |
| Network Subnet | `255.255.255.0` |
| Default Gateway | `192.168.18.1` |

I then performed a Ping Scan using the following command:

```bash
nmap -sn 192.168.18.202/24
```

The initial scan identified two live hosts on my local network:

| IP Address | Device |
|---|---|
| `192.168.18.1` | Huawei Router (Default Gateway) |
| `192.168.18.202` | My Windows Laptop |

The scan also provided MAC address information for detected devices.

- **Router MAC:** `40:EE:DD:69:8B:6C`


**Learning Outcome:**

This activity helped me understand live host discovery, IP and MAC address identification, subnet scanning, and basic network reconnaissance.

---

## 5. Risk Analysis

During Week 2, I learned that footprinting and network scanning are important cybersecurity activities, but they can also involve security risks if they are not performed carefully.

### 1. Information Disclosure

WHOIS, WhatWeb, Nslookup, and DNSRecon can reveal publicly available information about a domain, including IP addresses, name servers, website technologies, and DNS records. Attackers may misuse this information to understand a target's infrastructure.

### 2. Website Technology Exposure

WhatWeb can identify technologies and software versions used by a website. Attackers may use exposed version information to search for potential weaknesses.

### 3. Web Server Information Exposure

cURL can reveal information about web servers, application technologies, and redirect behavior through HTTP response headers.

### 4. Firewall Detection

WAFW00F can identify the presence and type of a Web Application Firewall. This information may help attackers understand the security technologies protecting a website.

### 5. Network Scanning Risks

Nmap and Zenmap can identify live devices and network information. Unauthorized or aggressive scanning may generate unusual network traffic, trigger security alerts, or affect network performance.

### 6. Unauthorized Access and Privacy Risks

Scanning devices without permission may violate privacy and security policies. Network discovery and reconnaissance should only be performed on systems for which proper authorization has been granted.

### Risk Mitigation

To reduce these risks, I performed reconnaissance and network scanning within the scope of authorized practical exercises. I also learned the importance of protecting sensitive network information, keeping software updated, and using cybersecurity tools responsibly.

---

## 6. Recommendations

1. Regularly update website software, plugins, and security configurations.
2. Protect sensitive domain and network information from unnecessary exposure.
3. Use Web Application Firewalls and configure security rules properly.
4. Monitor network traffic and regularly check for unknown or unauthorized devices.
5. Perform footprinting and network scanning only with proper authorization.
6. Continue practicing cybersecurity tools to improve technical knowledge and skills.

---

## 7. Conclusion

During the second week of my internship at NetworkWalk, I gained practical experience in footprinting and network scanning using Kali Linux tools and Zenmap.

I learned how to gather domain information, identify website technologies, examine DNS records, inspect HTTP headers, and detect Web Application Firewalls. I also practiced discovering live hosts and identifying devices on my local network using Nmap.

Overall, these activities improved my understanding of network reconnaissance and basic cybersecurity techniques. They also helped me develop practical skills in using cybersecurity tools and analyzing network information.

---

## 8. Evidence Collected

Screenshots from the practical activities are included below as evidence of the work performed.

### Module 1: Footprinting Using Kali Linux Tools

**1. WHOIS Results**

![WHOIS Results](evidence/module1/whois.png)

**2. WhatWeb Results**

![WhatWeb Results](evidence/module1/whatweb.png)

**3. cURL Results**

![cURL Results](evidence/module1/curl.png)

**4. WAFW00F Results**

![WAFW00F Results](evidence/module1/wafw00f.png)

**5. DNSRecon Results**

![DNSRecon Results](evidence/module1/dnsrecon.png)

**6. Nslookup Results**

_Add your Nslookup screenshot here._

### Module 5: Zenmap-Based Network Scanning

**1. Network Discovery / Ping Scan**

![Zenmap Ping Scan](evidence/module5/zenmap-ping-scan.png)

**2. Network Topology**

![Zenmap Network Topology](evidence/module5/zenmap-topology.png)

---

**Internship:** NetworkWalk  
**Week:** 2  
**Modules Completed:** Module 1 and Module 5  
**Focus Areas:** Footprinting, Reconnaissance, and Network Scanning
