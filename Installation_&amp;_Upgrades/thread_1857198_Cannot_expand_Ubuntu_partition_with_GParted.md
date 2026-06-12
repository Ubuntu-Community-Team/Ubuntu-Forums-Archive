---
title: "Cannot expand Ubuntu partition with GParted"
date: 2011-10-09
forum: Installation &amp; Upgrades
---

### Post by bontrager.nathan on 2011-10-09
I discovered after installing Ubuntu that Windows 7 allocated it a very small portion of the harddrive.  I was able to use GParted to shrink the Windows partition, however, I am unable to expand the Ubuntu partition.  Below is a screenshot of how my harddrive is currently partitioned via GParted:
[IMG]https://lh3.googleusercontent.com/-d-H8MRiqrUs/TpJMl5Sd4BI/AAAAAAAAAaw/gt-asW_eYlQ/s800/gparted.png[/IMG]
When I shrank the Windows partition (dev/sda2) it left all the unallocated space in the middle.  I am able to move/resize dev/sda5 (which is the one immediately to the right of the unallocated space and is shared drive accessible from both Windows and Ubuntu that already was set up when I got the laptop, a Lenovo G470) but when I then try to resize dev/sda4 (where Ubuntu is installed) it will not let me enlarge or move it, only make it smaller.  
dev/sda4 was previously flagged as "diag" but I changed that thinking it might allow expansion, which it did not (both via the boot CD and the version running in Ubuntu).

---

### Post by oldfred on 2011-10-10
You do not have a partition for Ubuntu. It looks like a wubi install.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Resize wubi - bcbc
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by www.rzr.online.fr on 2011-10-16
I did repart my g470 and only kept the 1st and last part
resized win7 one to 64 GB and OKR even worked...

-- 
[http://rzr.online.fr/q/lenovo](http://rzr.online.fr/q/lenovo)

---

