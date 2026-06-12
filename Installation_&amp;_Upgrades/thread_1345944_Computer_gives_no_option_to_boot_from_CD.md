---
title: "Computer gives no option to boot from CD"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by anthony62490 on 2009-12-04
OK, I'm not entirely sure of the name of this computer. The sticker on the back says that it's an HP Pavilion 700, the case itself says HP Pavilion 783c. Either way, when I put the CD in to install, It powers up, displays the HP splash for a few seconds, and then boots from the hard drive. No bootup procedures, no chance to configure the BIOS, nothing. Is there any way to force a BIOS check, or something along those lines?

---

### Post by TenPlus1 on 2009-12-04
When the HP logo appears press [F1] to enter bios and double check that the boot device order is CD then Hard-drive so you can boot from a disc...

---

### Post by efflandt on 2009-12-04
Look at the HP splash screen when you boot (but you have to look fast).  I forget if F1 or F2 gets you into CMOS setup.  But on my older HP 530n (from 2004) **Esc** allows me to chose boot device, and I am able to boot from DVD, CD, live/install iso on bootable USB stick (created with USB Startup Disk Creator), or WD Passport USB drive with regular 64-bit Ubuntu 9.10 installed containing grub2 in its mbr.

The key to select boot device might be either **Esc** or **F12** depending upon BIOS (unless someone disabled that in your BIOS).

---

### Post by anthony62490 on 2009-12-04
Thanks guys. That's about as simple as it gets. On my old PC, I had to press delete to get into the CMOS, so that's what the confusion was.

---

