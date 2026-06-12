---
title: "Ubuntu Server upgrade - problem with &quot;winbind&quot;"
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by tgrossner on 2008-01-09
**I am having a problem with the upgrade of winbindd, see below. Has anyone ever seen this or know of how to fix this?**

Reading package lists... Done
Building dependency tree
Reading state information... Done
winbind is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up winbind (3.0.26a-1ubuntu2.3) ...
 * Starting the Winbind daemon winbind
   ...fail!
invoke-rc.d: initscript winbind, action "start" failed.
dpkg: error processing winbind (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 winbind
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

