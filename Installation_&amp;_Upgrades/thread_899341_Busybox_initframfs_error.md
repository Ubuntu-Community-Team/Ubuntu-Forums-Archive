---
title: "Busybox initframfs error"
date: 2008-08-24
forum: Installation &amp; Upgrades
---

### Post by mkoonstra on 2008-08-24
I have a problem installing ubuntu 8.04 on my system. I have read a few threads about this error, but have not found a (complete) working solution yet.

The error happens with both the installation and/or starting the live CD.

First, my system specs:

AMD Athlon X2 4800+
ATi Radeon 1950 Pro
MSI K9A Platinum (RD580/X3200 chipset)
Samsung Spinpoint T166 400gb S-ATA HDD
2 GB of Kingston ValueRam

The system is not overclocked and is working perfectly using Windows XP.

I have read a few topic in the forum, advising me to add some parameters to the end of the boot options. I have tried the following options:

**pci=nomsi**
Did no change, same error

**irqpoll**
No change, same error

**all_generic_ide**
Sometimes starts the live cd correctly, but when it does, the disk is not seen.

**pci=nomsi irqpoll all_generic_ide**
Works most of the time, but no input devices (usb) work.

Checking the CD for error succeeded with live CD, no errors. (Confirmed this in windows). Also reburning slower (4x) did not do any results.

Changing mode for SATA controller (was set to Native IDE):

AHCI: Same error
RAID: Same error

Can anybody help me with this?

---

