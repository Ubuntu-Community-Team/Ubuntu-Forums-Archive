---
title: "Blank screen after GRUB on install - Asus X550C"
date: 2013-09-04
forum: Installation &amp; Upgrades
---

### Post by jason-barnabe-gmail on 2013-09-04
I have an Asus X550C series laptop. I'm trying to install Ubuntu 13.04 64-bit via a USB stick. I've created the USB stick via Ubuntu on another computer. I've verified the md5sum of the disk. After going through Windows 8's advanced startup, I told it to boot via the USB stick. I get the Grub screen giving the options:

Try Ubuntu without installing
Install Ubuntu
OEM install (for manufacturers)
Check disc for defects

I've tried all options except OEM install, and they all result in a black screen. I've tried editing the boot line per [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535) , replacing "quiet splash" with "nosplash --verbose text" or "nosplash --verbose single" and there is no difference - it still just goes to a black screen. I've also tried adding "nomodeset", "noacpi", "acpi_osi=Linux", and "video=1280x1024-24@75" - still nothing.

Any advice would be appreciated.

---

### Post by jason-barnabe-gmail on 2013-09-04
Got it going after finding [http://ubuntuforums.org/showthread.php?t=2156880](http://ubuntuforums.org/showthread.php?t=2156880) - needed to disable "Secure Boot Control" in BIOS.

---

