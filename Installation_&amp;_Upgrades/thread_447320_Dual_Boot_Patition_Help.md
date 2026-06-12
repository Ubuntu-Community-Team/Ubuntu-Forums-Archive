---
title: "Dual Boot Patition Help"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by darussian12 on 2007-05-17
Is there an official/proper way to get rid of a dual boot setup of Vista and Ubuntu. I want to be done with Vista and have no grub appear, but automatically boot into ubuntu. I want to use the freed space from deleting the Vista partition and expand my /home partition. I was wondering how to do it w/o screwing my partitions and losing imp stuff in my /home parition. Another words what program would I use to delete Vista and get rid of Grub and be able to blow up /home partition. Thank you

---

### Post by mikewhatever on 2007-05-17
Grub is the boot loader that boots both Vista and Ubuntu, so you can't get rid of it. You can hide its menu and set the time out to 1-2 seconds. Check this page [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
To delete existing partitions, use Gparted live CD [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

