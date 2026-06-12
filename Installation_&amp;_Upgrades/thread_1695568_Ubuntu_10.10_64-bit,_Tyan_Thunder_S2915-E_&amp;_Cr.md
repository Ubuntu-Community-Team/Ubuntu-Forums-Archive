---
title: "Ubuntu 10.10 64-bit, Tyan Thunder S2915-E &amp; Crucial CT256M225 256GB SSD"
date: 2011-02-26
forum: Installation &amp; Upgrades
---

### Post by allbread on 2011-02-26
I am attempting to install Ubuntu 10.10 (64-bit) on a Crucial 256GB SSD.  Currently I have a working install of Ubuntu running on the board off  of a spare Hitachi 250GB drive however I ultimately want my primary boot  partition on the SSD for performance reasons. 

Tyan Thunder S2915-E
2 x Opteron 2378 / 32GB DDR667-RE
EVGA GeForce 275 GTX / Tuniq 1000W PSU
Crucial 256GB M225 SSD (boot)
ARC-1120 PCI-X / 3 x 2TB Hitachi 7200 RAID5 (data)

I am having persistent issues getting Ubuntu to recognize (correctly)  the Crucial 256GB SSD. Although the SSD is recognized in the BIOS the  Ubuntu installer fails to register it as a viable partition on it's  first pass. If I reflash the BIOS of the SSD (using the "reflash" switch  on front) the drive is now recognized as a 256.1 GB partition (which I  think is erroneous, it should be more along the lines of 238 GB).

I have found advice online stating that the SATA controller must be set  to AHCI mode however I cannot find any corresponding setting in the  BIOS.

How do I go about installing Ubuntu 10.10 on a CT256M225 SSD?

---

### Post by allbread on 2011-02-26
I've found a thread that seems to indicate that this might be due to a bug:

[http://ubuntuforums.org/showthread.php?p=8690795#post8690795](http://ubuntuforums.org/showthread.php?p=8690795#post8690795)

...but I'm having some trouble implementing an immediate solution from  the details of the thread - at least, I don't really know how to pass  the kernel boot parameters described in the thread, if indeed this is  the workaround the author is suggesting.

Anyone have any advice for me?

---

### Post by mörgæs on 2011-02-26
Here is something on boot parameters:
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

It is written for a live CD, but most applies to a regular installation as well.

---

