---
title: "Unable to install Ubuntu/Lubuntu 15.04 &quot;ACPI PCC Probe Failed&quot;"
date: 2015-07-07
forum: Installation &amp; Upgrades
---

### Post by tom171 on 2015-07-07
I seem to be having the same problem on multiple PCs with version 15.04 64-bit.  I tried to install Ubuntu 15.04 on one PC.  I currently have Win 7 Pro 64-bit on one hard drive and OpenSUSE 13.2 64 bit on the other hard drive, trying to run the cd for Ubuntu 15.04 with just the openSUSE hard drive connected and getting error right away that says 'ACPI Probe failed'.  It then goes to the Ubuntu screen where it just says Ubuntu and has the dots underneath it likes its trying to load, but never does.

Now I'm at a different PC that has run both Windows 7 64bit and Ubuntu 14.04 64 bit, and trying to load Lubuntu 15.04.  I'm getting the same error 'ACPI Probe failed' when trying to load the CD.  Then it goes to the Lubuntu screen like its trying to load, but never does.

Same issue with 2 different installations.  Disks burned with different PCs and trying to load them on different PCs and I'm getting the same error and issue.  Has anyone else run into this?

Please let me know if I can provide more information.

---

### Post by dino99 on 2015-07-08
PCC probe is only met with recent hardware; yours are missing that chipset feature; that's all, nothing to worry about.

---

### Post by tom171 on 2015-07-08
Apparently I have a bad dvd drive in both PC's.  One is an 8 year old desktop and the other is a 3 year old laptop.  Both dvd drives can play regular cds, dvds, and burn Ubuntu CDs, but apparently they are not good enough to load an Ubuntu installation.  Put a new drive in one and it loaded right up and same issue with the other one.

---

### Post by grahammechanical on 2015-07-08
That error message should not stop Ubuntu from loading. I have been seeing it since about half way through the 15.04 26 week development period. I am still seeing it 2 months into the development period of 15.10. It never stops Ubuntu from loading.

The screen with the dots is the part where the live session detects the hardware and decides what hardware modules to load. It should eventually to to a live session desktop. You should see hard disk activity during this period.

The DVD drive might need cleaning.

[http://smallbusiness.chron.com/clean-laptop-dvd-drive-53900.html](http://smallbusiness.chron.com/clean-laptop-dvd-drive-53900.html)

Regards.

---

