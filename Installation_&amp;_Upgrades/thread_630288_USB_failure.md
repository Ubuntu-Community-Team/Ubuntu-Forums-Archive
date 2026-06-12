---
title: "USB failure"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by Richard Proctor on 2007-12-03
whenever i load my pen drive i can view the files in the explorer fine...but when i try and copy the files to the computer or upload files the connectin dies and i get a "forecful ejection of device" message pop up

why is this happening and how do i fix it?

---

### Post by Pumalite on 2007-12-03
What format and permissions does the USB have?

---

### Post by williambertram on 2008-07-22
I have similar problems.  My various USB drives always mount read only.  Is it supposed to work like that?  Also, when I attempt to file copy, some of the files will copy, then the drives are mysteriously unmounted.

Tried with multiple USB hubs.  The one integrated in my motherboard, the Belkin 5 port USB 2.0 PCI card, they all fail.  All mount automatically with rwx, and do not have this problem in XP sp2.

One of the drives is a Seagate ATA 100 3.5" hard drive in a USB enclosure.  I can take the drive out of the enclosure, plug it into the ATA controller, and it works flawlessly.  Plug it back into USB, it dies during file copies.  Drive is verified working in xp sp2 in the USB enclosure and attached directly to the ATA controller.  Also have duplicated with SimipleTech, Sony, and Belkin multi-card readers (all USB 2.0) using an assortment of SD, MS, CF, XD cards.

One work-around I've found is to do a sudo cp, but this also occasionally fails.  I'm fine with this, but I would imagine the general end user expectation is to plug the device in, have it automatically mount rwx, and not blow up on file copies.

---

