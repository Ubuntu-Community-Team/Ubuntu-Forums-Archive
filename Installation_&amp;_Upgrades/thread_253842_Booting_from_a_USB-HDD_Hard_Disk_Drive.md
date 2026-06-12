---
title: "Booting from a USB-HDD Hard Disk Drive"
date: 2006-09-09
forum: Installation &amp; Upgrades
---

### Post by anding on 2006-09-09
Hi,

I have been searching diligently but this particular problem does not seem to have been posted before.  I can't boot Ubuntu from a USB-HDD  :confused: !

**Situation:**

* Shuttle SB61, with BIOS that supports USB-HDD booting
* IO DATA 250GB USB2.0 HDD, partitoned as follows:

    1 Bootable 100GB, Primary, Linux
    2 8GB, Primary, Linux Swap
    3 130GB, Primary, FAT32

* Ubuntu 6.06.1 installed on partition 1 from the LiveCD

**Problem**

* After restart "non-system disk" error when attempting to boot from USB-HDD

Any ideas would be much appreciated! :)

---

### Post by anding on 2006-09-09
I found the solution by accident :| .  When I also have, in addition the the USB HDD, a USB flash memory plugged in at power on, then boot from the USB HDD boots fine.   I guess this is a BIOS issue.

---

