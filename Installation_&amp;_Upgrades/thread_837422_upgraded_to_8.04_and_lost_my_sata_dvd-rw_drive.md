---
title: "upgraded to 8.04 and lost my sata dvd-rw drive"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by coffee on 2008-06-22
I upgraded my system yesterday to 8.04.  Every thing seemed to work fine until I tried to use my dvd drive today.  The system dose not see it at all,  I had use of it before the upgrade and then it was gone.

If this can not be fixed I will be going back to 7.10.

---

### Post by Pumalite on 2008-06-22
Go to System>Administration>Software Sources>Open up all your repos; including partner, proposed, updates and backports. Ignore src; unless you have a special need for them. Reload. Then:
sudo aptitude update
sudo aptitude dist-upgrade
Report back.

---

### Post by coffee on 2008-06-23
Hello Pumalite

> **Pumalite said:**
> Go to System>Administration>Software Sources>Open up all your repos; including partner, proposed, updates and backports. Ignore src; unless you have a special need for them. Reload. Then:
sudo aptitude update
sudo aptitude dist-upgrade
Report back.

I did as you suggested and the dvd drive is still not recognized.

Not sure if this is related but another new thing with the upgrade is, during boot it lags "waiting for root".  After a minute or two the system boots up fine.  And then after I log in it takes a bit for my system load to drop down. 

I am not running compiz or anything fancy just gnome.:confused:

---

### Post by Pumalite on 2008-06-23
Try installing linux-generic

---

### Post by coffee on 2008-06-23
I tried booting with 2.6.22-15-generic kernel and my drive is recognized.

thanks for the help

---

### Post by Pumalite on 2008-06-23
You are welcome. Good luck.

---

