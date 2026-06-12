---
title: "Installing from a thumb drive"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by keval on 2008-03-18
Greetings.
I dropped my Satellite laptop a long time ago, jamming the CD drive beyond reasonable repair.  I'm trying to upgrade to 7.10 and am trying to do so with a thumb drive.  In a nutshell, I've downloaded the ISO image onto the stick, extracted the files, and adjusted my bios to boot from HDD first (and adjusted the HDD order to USB->HDD).  However, when I go to boot, I get the following error message:
"Invalid system disk
Replace the disk, then press any key to continue"

Any thoughts on what might be going on here?

Thanks,
Kevin

---

### Post by Cresho on 2008-03-18
[http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/](http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/)

---

### Post by keval on 2008-03-18
Thanks.  I clicked on the link and followed directions (although the link was written for someone installing ubuntu on a Windows system).  However, when I rebooted, I got the following:
" Syslinux 3.11 ...
Could not find kernel image: linux
boot:    "
Any thoughts?
Thanks,
Kevin

---

### Post by az on 2008-03-18
See here for clear instructions:

[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch#head-78b0db78435f28e95edbd38e14148a42c1dc4e00](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch#head-78b0db78435f28e95edbd38e14148a42c1dc4e00)
(Just create a filesystem greater than 200MB.  The squashfs image on the desktop cd is something like 650 megs...)


As for your problem, your bootloader configuration is not properly set.

---

### Post by Cresho on 2008-03-18
yeah do that one on top.  if that one fails, then I have another solution.  I actually made a bootable thumbdrive and installed ubuntu in the eeeasus.  ill keep track of this post.

---

