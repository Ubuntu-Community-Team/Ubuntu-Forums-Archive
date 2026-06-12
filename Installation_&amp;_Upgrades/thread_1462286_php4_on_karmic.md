---
title: "php4 on karmic"
date: 2010-04-25
forum: Installation &amp; Upgrades
---

### Post by dudley4 on 2010-04-25
For legacy reasons I need to install PHP4 with apache2 on server 9.2. I cannot install libapache2-php4 for the following reasons. Is there a way out of this? 

root@d410a:/etc/apt# apt-get install libapache2-mod-php4
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libapache2-mod-php4: Depends: apache2-mpm-prefork (> 2.0.52) but it is not going to be installed
E: Broken packages

---

