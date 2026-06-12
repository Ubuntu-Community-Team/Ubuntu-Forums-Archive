---
title: "Karmic Does Not Recognize my hdd"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by gonsalvr on 2010-01-06
Last night I booted up and got the black screen, and it would not boot. Can't find your /etc/home/fstab file or something along those lines I did not write it down. I got out my thumb drive and reinstalled Ubuntu 9.10, when I got to the partition phase I did a manual install and instructed Ubuntu to load onto /dev/sda1 /. I had previously partitioned this 160Gb drive with 41 Gb for root and 113 for my /home files and left 6.2 for Swap. Now it sees my second partition as 119 /dev/sda2 extended and Unrecognized. Unfortunately all my files are on that partition and I can't figure out how to tell Ubuntu to configure that partition as my /home . I really do not want to re-install and wipe that partition.  Can gparted fix this dilemma? I thought I was being so good by creating a boot partition so that I could upgrade in the future without affecting the rest of my files. :(
Thanks

---

### Post by milea on 2010-01-07
As i suppose you should go for the seven partition ( /boot, /, swap, /home, /tmp, /var, /usr, /usr/local) and keep your data in /usr/local. if your system crash then the scenario your data will be safe. And if you go for new installation all the partition except /usr/local will be formatted.  

In your scenario there are only three partitions and as your data is on home partition your entire hard disc get formatted with home or you will get less space if you do not format home partition for your new installations 

you can recover your system at any point if there is a problem in FStab and there are seven partitions.

---

