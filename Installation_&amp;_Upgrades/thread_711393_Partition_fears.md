---
title: "Partition fears"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by Steelbak on 2008-02-29
When I begin install from live cd on XP and partition comes up, it asks to shrink windows partition but is in RED print. Everything else is black print. That scares me into quiting the install.  This is important machine, and only machine to run our business.  Is it normal, or does it mean I should stop?

---

### Post by Pumalite on 2008-02-29
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk, boot from it and resize XP. (right click on XP and choose 'resize from menu. Format created space ext3. Install Ubuntu, go Manual and chose the partition you made. There, give at least 10 GB for '/'. 1 GB for /swap, the rest for /home. Then press 'Forward'
Backup everything first as a matter of good practice.

---

