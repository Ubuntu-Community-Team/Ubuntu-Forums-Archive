---
title: "Install Failing on Sata Detection"
date: 2005-02-19
forum: Installation &amp; Upgrades
---

### Post by psychomonkey on 2005-02-19
Hello,

I'm kind of new to Ubuntu having only installed it once under a VM. I'm actually trying to install it on an actual system. The system has 2 Ide harddrives and a 160GB Sata Hd which I have a pci sata controller card attached. When I start normal installation, the in hardware detection fails on finding usb devices (I have an external cd burner and a usb hub), but once I unplug those the installation continues. After that it always fails at 92% trying to load the modules for the sata. I've tried Mandrake 10.1, Red Hat 9, Fedore Core 3 and Ubuntu and non of them will install correctly due to that device. The chipset is labeled as Silicon Image 3112. I would really prefer to use Ubuntu, but can anyone tell me where I can find if this chipset is supported?

Please help.

---

### Post by Dr Bill on 2005-03-01
[QUOTE=psychomonkey]Hello,

I'm kind of new to Ubuntu having only installed it once under a VM. I'm actually trying to install it on an actual system. The system has 2 Ide harddrives and a 160GB Sata Hd which I have a pci sata controller card attached. When I start normal installation, the in hardware detection fails on finding usb devices (I have an external cd burner and a usb hub), but once I unplug those the installation continues. After that it always fails at 92% trying to load the modules for the sata. I've tried Mandrake 10.1, Red Hat 9, Fedore Core 3 and Ubuntu and non of them will install correctly due to that device. The chipset is labeled as Silicon Image 3112. I would really prefer to use Ubuntu, but can anyone tell me where I can find if this chipset is supported?

Please help.[/QUOTE]
 Same problem.  Freezes at 91% on Raid install.  I have Sis 180/1 Raid/SATA controllers on ASUS P4s800D-E board.  Interesting enough, the Warty "Live" iso **works** on my SATA drive:  reads and writes to a FAT32 partition.  I have been searching on and off over a month for an answer to no avail.  Have you found any answers that a newbee like myself can use?

I am about to try a Slackware distro with (advertised) SiS support.   Good luck.  Dr Bill

---

### Post by stamy on 2005-03-06
I had exactly the same problem, and the source was my old hardware.

I use a cheap PCI sil3112 card (sata raid) and it hang's on 92 percent on my old Asus (3 years old with KT266) and on another PC Shuttle it is working fine (the same PCI card !!!!).

So if your plan was to upgrade your PC with a new SATA drive and this PCI external card, forget it and change your Motherboard too.

When you have already a new mobo the solution is to flash your bios, take a look at this forum:

[http://www.short-media.com/forum](http://www.short-media.com/forum)

Hope it help.

---

