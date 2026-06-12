---
title: "Grub: Dual Boot Feisty and Dapper"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by Oceola on 2007-09-05
I had Dapper installed on sdb and later on installed Feisty on sda. When feisty installed it commandeered the grub which I figured was OK and it noted Dapper as "other" operating system but the problem seems to be in the grub installed by Feisty not recognizing a kernel update in Dapper, which is booted from the Feisty grub.
The recent Dapper update to Ubuntu, kernel 29-686  from 28-686 shows up in the Dapper grub menu list but does not show up in the Feisty Grub menu list.

If I edit the Grub list in Feisty manually will it then recognize 29-686?
Will that resolve the issue? :confused:

---

### Post by adewale on 2007-09-05
well you could try that but make a backup of ur meun.lst first before doing anything.

---

### Post by rsambuca on 2007-09-05
That will work perfectly.

---

### Post by Oceola on 2007-09-06
Thank you, adewale and rsambuca. :)

Have edited the pretty colors and timeout for the list with gedit set to make a backup, even with privileged files it seems to work fairly well.  ;)

---

