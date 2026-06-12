---
title: "sudo apt-get problems"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by tsumiro on 2008-01-27
hey. i have a problem with using sudo. if i try doing anything that involves sudo apt-get install, i get this error...

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by jeffus_il on 2008-01-27
All the upgrade/update/Remove tools use the same underlying software "aptitude" from Debian. Each one will flag a lock file to show that it is using the system, since more than one update running at the same type could damage your installation. If one other of the update programs are running while you run apt-get, it will not be able to hold the lock because it is locked by another program. Check what is running when this happens.

---

