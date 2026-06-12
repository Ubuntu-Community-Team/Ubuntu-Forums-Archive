---
title: "Installer can't mount CD."
date: 2011-06-07
forum: Installation &amp; Upgrades
---

### Post by Perkins on 2011-06-07
I just got my hands on a machine with an Intel Pentium G620, and a Gigabyte H61M-D2P-B3 Intel H61 Motherboard.  The alternate installers will boot, but then can't mount the CD drive to actually install.  The liveCDs I've tried go through their bootloader, and then drop to initramfs.  Does anyone have any insight as to what I should try next?

---

### Post by Perkins on 2011-06-07
Of course, once I ask for help I figure it out...  For reference, this particular combination will default to using its SATA jacks as IDE ports...  I'm a little fuzzy on how, exactly that would work...  But now that I've set it to AHCI it's happy.

---

### Post by Pakana on 2011-09-22
Thank You!
Had same problem. now I'm just getting kernel panic :p

---

### Post by Perkins on 2011-09-22
Kernel panics generally indicate either badly unsupported hardware, or some kind of hardware fault.  There is an options section on the installer's startup screen to disable ACPI and other, occasionally problem-causing, services.  Try turning them all off and see what happens.

---

