---
title: "HP Installation Issue"
date: 2008-03-10
forum: Installation &amp; Upgrades
---

### Post by AdHavoc on 2008-03-10
Recently I decided to load Ubuntu 7.10 Gutsy Gibbon on my spare HP Pavilion zv6000 series laptop.  The LiveCD works fine and everything loads, except when I try to install, when I get to the partition manager (GParted), it will not let me resize my primary partition which currently houses Windows XP Professional.  There is always an error that will not let me resize the partition.  I made a LiveCD of GParted and attempted to resize from there, to no avail.  Does anybody have any suggestions to help me get Ubuntu on my laptop?

---

### Post by Pumalite on 2008-03-10
[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))
[http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/](http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/)
[http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)
[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

---

### Post by AdHavoc on 2008-03-10
> **Pumalite said:**
> [https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))
[http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/](http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/)
[http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)
[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

Note that I have the zv6000 and not the dv6000 series.  There are some major hardware differences between the two and anyways, none of those links address the problem I've been having.  All of the links say that I should install Feisty because of driver compatibilities, etc, but my issue is that the partitioner will not work correctly, which doesn't really have anything to do with which version of Ubuntu I'm using.

---

### Post by Pumalite on 2008-03-10
Try Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Resize XP (right click on XP), choose 'resize' from menu.

---

### Post by TimelessRogue on 2008-03-10
One method that I have used in the past is to use a partition manager such as Acronis (free fully functional trial download) while operating under Windoze to partition your disk assigning a partition to XP (the first), leaving the balance of the disk unformatted and then using that partition for your Ubuntu installation.  This method works just fine and I have recently used it successfully on my old HP n5000 laptop to install Gutsy alongside XP before sell it.  I, too, was encountering the problem you ran into and this solved it for me ...

Good luck ...

---

### Post by AdHavoc on 2008-03-10
> **Pumalite said:**
> Try Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Resize XP (right click on XP), choose 'resize' from menu.

I have already tried this and the same error comes up.  I think it is a problem with either A) The hard drive or B) GParted.

> **TimelessRogue said:**
> One method that I have used in the past is to use a partition manager such as Acronis (free fully functional trial download) while operating under Windoze to partition your disk assigning a partition to XP (the first), leaving the balance of the disk unformatted and then using that partition for your Ubuntu installation.  This method works just fine and I have recently used it successfully on my old HP n5000 laptop to install Gutsy alongside XP before sell it.  I, too, was encountering the problem you ran into and this solved it for me ...

Good luck ...

Thanks, I'll try this and post my results; crossing my fingers that it works.  Also, should I create another partition for linux-swap?  My laptop has 512mb RAM and I heard that the linux-swap size should equal the RAM.  Will Ubuntu automatically set aside a linux-swap partition?

---

### Post by TimelessRogue on 2008-03-11
You'll end up with two partitions ... one with Windoze and one unformatted, which will become your new Ubuntu installation formatted as ext3 during the installation.  When you install Ubuntu it will see the partitions as drives:  hda and hdb.  The installation should be pretty straight forward from that point with Ubuntu assigning the swap partition size for you as part of the process.

Though I tend to ride on the edge and don't, you just might want to make sure you have a backup of Windoze or at least your data before you start.  Good luck and enjoy ...

---

### Post by AdHavoc on 2008-03-11
I tried the demo but apparently you cannot resize the disk in demo mode.  Would Wubi work or would that come up with the same GParted error?

---

