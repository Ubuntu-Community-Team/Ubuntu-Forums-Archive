---
title: "Install CD locks up at menu, please help ASAP!"
date: 2007-03-04
forum: Installation &amp; Upgrades
---

### Post by mrogers on 2007-03-04
After a long while I've decided to upgrade my file server's motherboard and CPU. I put in some parts I had laying around: an ECS motherboard, 384MB ram, AthlonXP 1600+ processor (yeah that's an upgrade compared to what I had), and got the newest 6.10 release Ubuntu server install CD. I've installed Ubuntu many times before without trouble.

When the system boots, it reads the CD, shows me the nice Ubuntu menu with Install to the Hard Disk, Check CD for defects, ...etc. But now it is locked up. I can't press Enter, I can't select a different item on the list, and even Num Lock doesn't light up if I press that key.

Hardware I have hooked up right now (this all worked fine with 5.10 install): 1x NetGear gigabit NIC, 1x RealTek 10/100 NIC, 1x IDE controller card, 1x SATA controller card. There are no hard drives hooked up except for my primary one through the SATA controller for the installation process, and of course the CD-ROM through the motherboard's IDE.

Please help me figure this out quickly, I can't be without my file server for long!! Thanks!

---

### Post by mrogers on 2007-03-04
OK, well, as it turns out it's the SATA card causing the problem, and it doesn't seem to be exclusive to the Ubuntu install CD. Once the SATA card has loaded its BIOS, the keyboard doesn't work anymore. This is probably fixed with the BIOS update that's available for my motherboard, but I don't have any floppy drives and ECS's web site sucks...I haven't found a way to do it with a CD yet. CRAP.

UPDATE: I've got flashing with a CD down pat, but even the most up to date BIOS from ECS doesn't solve the problem.

---

