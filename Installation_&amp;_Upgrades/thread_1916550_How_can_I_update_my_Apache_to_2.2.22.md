---
title: "How can I update my Apache to 2.2.22?"
date: 2012-01-28
forum: Installation &amp; Upgrades
---

### Post by UlfDunkel on 2012-01-28
My Ubuntu server is frequently scanned by the Trustwave robots which now complain that I run Apache 2.2.20 and should fix an vulnerability issue by updating to v2.2.22.

I am not too familiar with the Apache updates, but "apt-get upgrade" did not include Apache on my machine.

Do I have to wait until this version has been packaged for aptitude?


For those who are interested, here is the issue found by Trustwave: 

**Apache HTTP Server Reverse Proxy/Rewrite URL Validation Vulnerability**

Severity: Medium
PCI Status: Fail
CVE: [http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2011-4317](http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2011-4317)

**Description:**
The mod_proxy module in the Apache HTTP Server 1.3.x through 1.3.42, 2.0.x through 2.0.64, and 2.2.x through 2.2.21, when the Revision 1179239 patch is in place, does not properly interact with use of (1) RewriteRule and (2) ProxyPassMatch pattern matches for configuration of a reverse proxy, which allows remote attackers to send requests to intranet servers via a malformed URI containing an @ (at sign) character and a : (colon) character in invalid positions.
[B]
Remediation:[/B]
This issue has been fixed in httpd 2.2.22-dev or later releases.  It is highly recommended that when upgrading that the latest available version from the vendor is utilized. Alternatively this finding may be addressed by disabling mod_proxy, and/or by disabling a reverse proxy (if one is in place), and/or by disabling the use of RewriteRule and ProxyPassMatch.

---

### Post by UlfDunkel on 2012-01-31
Is my question too stupid? I'd be glad to receive any comment.

---

### Post by dunnomattic on 2012-02-01
I don't know if this will specifically help you, but I ran across this while investigating a similar report on our servers regarding CVE-2011-3368 and CVE-2011-3348.  Turns out, the latest oneiric version of Apache in the stock repositories is 2.2.20-1ubuntu1.1 -- so these vulnerability reporting mechanisms see the version as being 2.2.20 and report you as having a Severe/Critical unpatched risk.  However, the customizations applied to that 2.2.20 base (described by the "-1ubuntu1.1") actually includes the patches for those two vulnerabilities in my case.

reference: [https://launchpad.net/ubuntu/+source/apache2/2.2.20-1ubuntu1.1](https://launchpad.net/ubuntu/+source/apache2/2.2.20-1ubuntu1.1)

I would search recent changelogs and keep an eye on upcoming changelogs over the next couple of weeks for backported patches rolled in to 2.2.20.

---

### Post by UlfDunkel on 2012-02-02
Thank you for this really helpful reply.

---

### Post by mpatrick2 on 2012-02-13
[FONT=&quot]We have a similar issue, our servers (Ubuntu version 11.10) are being automatically scanned and have reported vulnerability: CVE-2011-3639. 
 Does anyone know if the latest version of Apache in the repository solves this issue? Is there any supporting documentation that shows it has been fixed? 

Is there an easy way to tell if Apache has been patched?

Thanks

[/FONT]

---

