---
title: "Samba - &quot;The semaphore timeout period has expired&quot;"
date: 2017-11-20
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2017-11-20
Ubuntu 16.04.3 I installed a bunch of upgrades over the weekend. I am getting the following error now when attempting to connect to the Samba domain from a Windows client:

"The semaphore timeout period has expired"

testparm produced no errors and I made no changes to smb.conf. Samba Version 4.3.11-Ubuntu

It appears that something in the upgrade change some network settings. The mailserver on the same machine does not seem to be responding either.

---

### Post by rsteinmetz70112 on 2017-12-12
Remoiving courier and reinstall postfix and sqwebmail seems to have resolved the issue. Still not sure what caused the problem.

---

