---
title: "Securing a FOG installation"
date: 2010-11-30
forum: Installation &amp; Upgrades
---

### Post by abasel on 2010-11-30
I've done the following, but the line "c:\Program Files\FOG\HostnameChange.dll with this File" refers to a windows machine. How does this apply to an ubuntu machine?

> Change FOG-OpenSource-Imaging to anything you like, just remember what you change it to, as you will need it later.
Then click File -> Save All.
Then click Build -> Build Solution.
This will recompile the hostname change module with your unique key.
Now navigate to "FOG Service\src\FOG_HostNameChanger\bin\Release"
Copy only the file HostnameChange.dll to some place safe.
Every time you install the FOG service you must replace the file:
c:\Program Files\FOG\HostnameChange.dll with this File

---

