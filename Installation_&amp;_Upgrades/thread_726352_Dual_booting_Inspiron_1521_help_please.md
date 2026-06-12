---
title: "Dual booting Inspiron 1521 help please"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by HelpIsNice on 2008-03-16
Hi I got a dell insiron 1521

Hardware: AMD 64x2 2.2ghz, ATI Radeon Xpress 1270 video, integrated sound (ATI SBx00 which shows as HDA-Intel using STAC 9205 chipset), built-in Omnivision webcam 2gig RAM, 160gig SATA HD 8X DVD+/-RW DL, Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

Ok Ive never dual booted before but i looked at some of the how to articles and i thought i  had it down.I first reformatted my hdd and made it so i had unallocated space to install ubuntu on.I tried to install it but it got to the gtf partition 7 and it failed.I tried 3 times then turned my pc off and when i tried to restart it said press f1 to retry boot lol.

So i read this [http://ubuntuforums.org/showthread.php?t=607378](http://ubuntuforums.org/showthread.php?t=607378) and somebody said that it only allows 4 partitions?So I guess i wont install dell media direct, but will that ensure that there will only be 4 partitions?Ive have had so much trouble with this and any help would be nice.BTW i tried getting help for dell, firedog, ect, but no help from them with dual booting on my computer.Any help to what i did wrong and how i can suceed next time will be excellent, thank you.

---

### Post by Pumalite on 2008-03-16
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)
You are allowed 4 primary partitions per hard drive. Have 3 and from the third make an extended partition, within which you can put as many logicals as you want. Windows needs primary, but Ubuntu is happy in a logical.

---

### Post by HelpIsNice on 2008-03-16
wow thanks you guys are fast :smile:

---

### Post by Pumalite on 2008-03-16
Good luck.

---

