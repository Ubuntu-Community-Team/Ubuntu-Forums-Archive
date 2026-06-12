---
title: "Removing Ubuntu On Vista/Ubuntu dual boot?"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by Tridion2000 on 2007-06-21
Could someone please give me the steps required to safely remove Ubuntu from a Vista/Ubuntu dual boot PC. Had enough of Ubuntu and would rather use the disk space for something else.

---

### Post by FRuMMaGe on 2007-06-21
> **Tridion2000 said:**
> Could someone please give me the steps required to safely remove Ubuntu from a Vista/Ubuntu dual boot PC. Had enough of Ubuntu and would rather use the disk space for something else.

Can't you just delete the partition?  You could even use the Ubuntu Live CD to remove it

---

### Post by timcredible on 2007-06-21
you can't just delete the partition because then you can't boot (the mbr has been changed to look for info on the linux partition).  you need to do a search on this.  booting with the windows cd and doing a repair on the mbr is needed (basically the windows cd will put the old mbr info back with an fdisk command, i think it's fdisk /mbr but do a search to make sure)

---

### Post by srirambond007 on 2008-01-23
Yes what these guys say are right ...just delete the linux partition and for vista as this forum is concerned ...just pop the dvd and on the first screen before installation u can see a small repair button on the left botton its actually words rather than button ...it works like a hyperlink....click on it will search for a OS and repair the mbr automatically 

VISTA ROCKS....Ubuntu keeps up.....

---

