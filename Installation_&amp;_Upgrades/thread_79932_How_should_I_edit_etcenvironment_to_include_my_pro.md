---
title: "How should I edit /etc/environment to include my proxy setting?"
date: 2005-10-21
forum: Installation &amp; Upgrades
---

### Post by Akhran on 2005-10-21
My proxy server IP address is 192.168.1.1. I finished the OS installation without the apportunity to key in my Proxy server's IP address. Subsequently, I have to do export http_proxy="http:192.168.1.1:8080" after each reboot for aptitude update to work. 

Read somewhere in forum that I can edit /etc/environment to include http_proxy's value so that I don't have to export after each reboot.

Do I just append HTTP_PROXY="http://192.168.1.1:8080" to /etc/environment?

Thanks !

---

