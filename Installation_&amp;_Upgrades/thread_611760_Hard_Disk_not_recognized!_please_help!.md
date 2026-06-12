---
title: "Hard Disk not recognized! please help!"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by Ionut_Romania on 2007-11-13
Hello!
I have a problem with my Fujitsu Siemens AMILO Pro V3515.
When i try to install Ubuntu LTS6.06 Drapper Drake it doesn't recognize my Hard Disk. I have a 80 GB SCSI HDD that came with my laptop. This drive currently has no partition on it. I can't download or upgrade ubuntu since there's no space to save the download in, and i would appreciate if anyone can give me some advice. I really like Ubuntu and i don't want to go back to windows xp.
Please help!
thank you

---

### Post by Triptol on 2007-11-13
If you really have a SCSI drive (kinda hard to believe with a laptop, but not impossible) what you need to do is make sure you have the right module loaded for your SCSI adapter. Don't know which one you have, but lspci might help you here. 

Once the adapter is loaded the HDD should be recognized.

---

### Post by vankampen92 on 2007-11-13
HI!!

I had a similar problem at booting time with my intallation and finally I found that it was my SATA controller 

([http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)). From AHCI to COMPATIBILITY.

Hope this help.

---

### Post by vankampen92 on 2007-11-13
HI!!

I had a similar problem at booting time with my intallation and finally I found that it was my SATA controller 

([http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)). 

I change my BIOS options of the SATA bus (from AHCI to COMPATIBILITY).

Hope this help.

---

### Post by santoxyz on 2007-11-26
your disk is SATA.
you need kernel >= 2.6.18 with builtin support for 
sata_via and ahci 

if you compile them ad modules you need an initrd

---

### Post by klhouse on 2007-11-30
I had a similar problem with a Western Digital hard drive.
Changing the jumper on the drive from Master to Single solved my problem.

---

