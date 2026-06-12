---
title: "Synaptic Error Message"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by orbilius on 2007-05-18
Hello.  I was installing checkGmail when I lost power to my PC.  I now have this error message when I load up Synaptic:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


When I run this in the terminal I get the following message:

dpkg: requested operation requires superuser privilege

My user account has full provlidges.  Anyone know what I am doing wrong?  thanks,

---

### Post by vigleik on 2007-05-18
sudo dpkg --configure -a. And make sure you close synaptic first.

---

