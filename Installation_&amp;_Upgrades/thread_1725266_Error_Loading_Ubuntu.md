---
title: "Error Loading Ubuntu"
date: 2011-04-09
forum: Installation &amp; Upgrades
---

### Post by fantab on 2011-04-09
I have installed Ubuntu on my EXTERNAL HARD DISK, however when I restarted my desktop I got a Black Screen and on the top was displayed "**Error Loading Operation System**".
 
I have set in my desktop board BIOS to boot from my External Hard Disk first, and have also enabled booting from USB Devices. [The idea is to let ubuntu load when Ext.HDD is connected and when it is not Windows should boot.] So I get the error message when Ext.HDD is connected. 
 
I have no problems with loading Windows (which means that I have installed my ubuntu and particularly GRUB at the right place. GRUB is installed on the same partition as Ubuntu).
 
I used 100GB of my EXT.Hard Disk space to install Ubuntu. From the alloted 100GB I created 3 partitions (Ext4): 20GB Primary(mount Point "/") -78GB Logical (mount point "/home")- 2GB Logical (Swap area).
 
I use Ethernet Cable to connect to Internet, however Ubuntu did not find it connected and during install I did not chose the option to "Download updates during installation". Also somehow my Windows time is affected (I have noticed during Ubuntu installation that the Time zone/time is not accurate)
 
 
What is it that I am doing wrong here? Please help me solve this issue.
 
Regards

---

### Post by fantab on 2011-04-09
I have figured it out...
 
I had wrongly installed GRUB on sdb1 when it should have been installed it on sdb. and when I installed GRUB correctly everything works to my satisfaction.

---

