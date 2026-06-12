---
title: "USB External Hard drive causes boot to fail"
date: 2007-04-01
forum: Installation &amp; Upgrades
---

### Post by drhiii on 2007-04-01
Have installed Desktop 6.10 very successfully on a Celeron 3gh box.  Everything, including all upgrades, working dandy.  

I plug in a USB external drive and it mounts and displays it properly.  Cool.  However, when I reboot the box with the USB plugged in, it never reaches GRUB but fails with a DISK failure.  

I checked the BIOS to make sure the boot sequence is correct (depending on the situation, it is HD first, or CD/HD if I am running a CD boot first).  There is nothing apparent to me that would redirect the boot sequence to an external device.

Thought anyone.   Will keep digging of course, but wondered if anyone had an idea or two?

tx, drh

---

### Post by DaOane on 2007-04-02
Your external USB harddisk may be listed as a harddisk in the BIOS and not as an external device. Open the harddisk-entry in the boot-sequence table an check if both the internal and external harddisks are listed and that the internal harddisk is listed first.

---

### Post by drhiii on 2007-04-02
Ah, I did not know there may be a second "location" in the BIOS that may affect this.  I will follow your advice, and thank you for your quick response.  Am finding the Ubuntu to be, after years of participation in others, most friendly and helpful...

drh

---

