---
title: "Dual Boot, 2 HDDs, GRUB doesn't load"
date: 2005-08-19
forum: Installation &amp; Upgrades
---

### Post by Velox Letum on 2005-08-19
Okay, so my setup is as follows

**[EDITED: More information]**

Intel Pentium 4 3ghz HTT
Intel Bonanza D875PBZ  (5 PCI, 1 AGP, 4 DIMM, LAN) (Mainboard)
Intel Canterwood i875P (Chipset)
1GB Coursair PC3200 DDR SDRAM
Seagate Barricuda 120GB SATA (Windows XP Drive)
Maxtor Diamondmax Plus 8 40gb ([K]Ubuntu Drive)
Nvidia GeForce FX 5950 Ultra 256mb
Intel(R) 82801EB Ultra ATA Storage Controllers (IDE Controllers)

IDE channel map
0
-0 CD-ROM (Master)
-1 EMPTY

1
-0 CD-ROM (Master)
-1 Ubuntu HDD (Slave)
Anyways, today I decided that I wanted to run [K]Ubuntu outside of VMware Workstation, so I dug out a pretty new, hardly used Maxtor Diamondmax Plus 8 40gb drive and install Ubuntu onto it, and set my BIOS to boot from the Maxtor drive, so that I could boot into XP or Ubuntu from GRUB. I ran through the installer, erased the Maxtor drive, installed without error, came to GRUB config, it said it detected Windows XP, I rebooted, set my BIOS's primary drive to the Maxtor drive so that it would be the HDD booted from (and confirmed in Boot Priority) as the Maxtor drive.

I rebooted, and it came to the point where I expected GRUB would appear, and a dash just blinked for about 5 seconds before (I assume) the BIOS moved on to my Seagate drive and booted up Windows. Did I miss something in the installer? Is something wrong with the second drive's MBR?

---

### Post by bela on 2005-08-19
Hi, 
what is your grub menu.list ?

have you declare your ubuntu in this file ?
by default , the grub waits 5 seconds and  run the default system declared in menu.list

best regards
bela :smile:

---

### Post by Velox Letum on 2005-08-19
[QUOTE=bela]Hi, 
what is your grub menu.list ?

have you declare your ubuntu in this file ?
by default , the grub waits 5 seconds and  run the default system declared in menu.list

best regards
bela :smile:[/QUOTE]
 The problem is, fresh out of an Ubuntu install I have no way of mounting and perusing menu.list. The whole problem is that after installing it, it pauses, showing a blinking slash, then blank, then Windows. This is after hitting Yes to writing the MBR on the 40gb drive, then using the 40gb drive as a boot HDD.

---

### Post by Velox Letum on 2005-08-19
Okay, I was able to find a Windows program to read an ext3 filesystem and I exported menu.lst from /boot/grub

[http://pastebin.com/340613](http://pastebin.com/340613)

---

### Post by Velox Letum on 2005-08-19
Using VMware workstation I made a virtual machine reading from that drive and it appears that GRUB is on there.

---

### Post by Velox Letum on 2005-08-19
Okay, posting more information because I am completely stumped.

[http://paste.ubuntulinux.nl/1401](http://paste.ubuntulinux.nl/1401) - Paste from sudo fdisk -l
[http://paste.ubuntulinux.nl/1402](http://paste.ubuntulinux.nl/1402) - Paste from /etc/fstab
[http://paste.ubuntulinux.nl/1403](http://paste.ubuntulinux.nl/1403) - Paste from /boot/grub/menu.lst

Anyways GRUB (after manually restoring it with root (hd0,0)) acts the same...just a blinking underscore-dash. I even tried with bootpart and NTLDR. Still the same. So I decided it was time for an experiment.

I opened up VMware Virtual Workstation 5, made a new Virtual Machine using the second (IDE) HDD as its HDD, set the node to IDE 1:1 (IDE channel 1, slave) as it is on my actual computer, started it up, and GRUB loaded fine, booted into Ubuntu and am now doing the post-install tasks. I'd much rather load into it directly though rather than loading Linux at all.

---

### Post by Velox Letum on 2005-08-21
Just wanted to say that my problem is solved  :grin:  :grin:  :grin: 

Apparently it didn't like being hdd (IDE2, Slave) but GRUB loaded fine (and after a reinstall, Ubuntu too!) once it was hdb (IDE1, Slave).  :grin:  :grin: 

*runs off to do post-installation tasks*

---

