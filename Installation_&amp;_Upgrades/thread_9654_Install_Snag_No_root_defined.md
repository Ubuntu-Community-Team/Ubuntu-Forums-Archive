---
title: "Install Snag: No root defined ?"
date: 2004-12-30
forum: Installation &amp; Upgrades
---

### Post by BillF on 2004-12-30
Hi I sure could use some help with installing Ubuntu on a laptop with XP installed using the following partitions as seen by the Ubuntu install application:

IDE Master (hda) 80 GB
	#1 Primary 58.4 GB Windows XP
	#5 Logical 4.1 GB (root flag on)  
	#6 Logical 518.1 MB Swap
	#7 Logical 16.8 GB  Ext3

As I proceed through the installation process to the point where I answer yes to partition the disks, I get the following message:

No root file system is defined

I wish to install Ubuntu to partition #5, however, I can't seem to go any further with the installation process. 

Thanks!

Bill

---

### Post by Rancoras on 2004-12-30
Are you selecting the option to manually edit the partitions?  If so, make sure you have the one where you want Ubuntu installed set to mount it at /

---

