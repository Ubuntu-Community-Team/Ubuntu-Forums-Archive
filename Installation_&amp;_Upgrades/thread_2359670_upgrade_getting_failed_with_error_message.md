---
title: "upgrade getting failed with error message"
date: 2017-04-26
forum: Installation &amp; Upgrades
---

### Post by shridhar-kapshikar on 2017-04-26
I have been trying to upgrade ubuntu 14.04 to 16 and during that the upgrade process getting failed with below error

Errors were encountered while processing:
 /var/cache/apt/archives/libjpeg8_8d1-2_i386.deb
 /var/cache/apt/archives/libjpeg8_8d1-2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I am wondering why upgrade getting failed. Any suggestions are welcome.

---

### Post by RobGoss on 2017-04-26
I would do a clean installation and avoid these kinds of problems, trying to do system upgrade can be 
problematic.  Backup any important files and data and go with a clean installation

---

### Post by sp40140 on 2017-04-27
As RobGoss mentioned. To be safe, just back important stuff and do clean install.
If that's not an option (for reasons your own), you can delete those two deb files in the error message and try to upgrade again.
I recently ran into this issue (however, it was after I moved to 17.04 and different application update). But deleting the deb file fixed error for me. 
And you can re-install those deb files again manually after upgrade.

---

