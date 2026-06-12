---
title: "Ubuntu does not install in BIOS IDE mode"
date: 2008-09-05
forum: Installation &amp; Upgrades
---

### Post by poriajay on 2008-09-05
Hi All,

 I have following configuration for my PC.

CPU : Intel E8400
Mobo: Asus P5Q Pro
GPU : Nvidia 8800GT
HD  : Seagate 400GB
RAM : 2GB Transcend

  First I have installed windows XP SP2 on C: drive (200GB Partion). After that I have created 3 more partion using Windows XP. 20 GB for Linux OS, 178 BG for Linux home, and 2 BG for Swap area.

  I tried to install Ubuntu 8.04 but Ubuntu Partition Manager Can not detect any file system on Hard Disk. I waited for 15 min. The screen on which it display partition does not have anything... no success. 

  Than I have changed BIOS hard disk setting from IDE Enhanced to RAID. Ubuntu Installed in this mode. But now Each time I need to load Ubuntu I need to change Storage Configuration from IDE to RAID. 

  Is there any clean way to install Ubuntu? Also When I load Ubuntu and I try to connect to Web using ADSL modem (LAN Cable) Ubuntu does not detect LAN Cable attached as my model LED does not glow for LAN Cable.

Thanks in advance.
Best regards,
Jayesh

---

### Post by Pumalite on 2008-09-05
Post:
lshw -C network

---

