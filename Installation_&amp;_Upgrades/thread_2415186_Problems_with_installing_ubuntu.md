---
title: "Problems with installing ubuntu"
date: 2019-03-22
forum: Installation &amp; Upgrades
---

### Post by lukas713 on 2019-03-22
Hello, 
I just got new PC and I wanted to install Ubuntu 18.04. When I set bootable KingstonDataTraveler USB as "priority", I got ubiquity and it loads fine. When I enter city, username... and OS start with installation, at the middle of installation i got "Installation crash" that warns me about nothing specific. It just says: "We're sorry, installer has crashed. Press next to send bug report...". There is no explanation why that's happening. I installed ubuntu with same usb last week on my Toshiba laptop, and everything was fine.

If I only "Try ubuntu" to read log files, I got "PCI bus error severity = corrected..." spam on my screen. 

What am I doing wrong?

---

### Post by ubname on 2019-03-22
I'd try to download again and use another usb (if you have) for a start ...

---

### Post by fra_pennaz on 2019-03-22
Moreover, some checks before start the installation:
- check the MD5SUM of the iso you downloaded is correct
- before booting ubuntu live or the installer, perform "check disk for defects" (it is somewhere in the usb live boot menu, sorry I don't have a drive to check where it is exactly now)

---

### Post by oldfred on 2019-03-22
What brand/model system?
And what video card/chip?
Some require extra boot parameters.

Have you updated UEFI and if SSD the SSD firmware?

---

### Post by lukas713 on 2019-03-22
I downloaded new ISO image and everything works fine.

---

