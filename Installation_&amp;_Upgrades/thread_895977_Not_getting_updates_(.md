---
title: "Not getting updates :("
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by silverbird on 2008-08-20
hi guys
i have some prob in upgradation
when i start update manager it shows the following error

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: _cache->open() failed, please report.

i am unable to open/modify/delete this lock file as it shows

Cannot open /var/lib/dpkg/lock: No application suitable for automatic installation is available for handling this kind of file.

please help
thanks

---

### Post by Pumalite on 2008-08-20
Is Synaptic or other apt-get processes running?

---

### Post by J$oney on 2008-08-20
Something must be using the package manager. Find out what ps is using it, and either kill it or restart into recovery mode and do the update, if this is for hardy I would suggest using recovery mode, you can change the mode during the login screen.

---

