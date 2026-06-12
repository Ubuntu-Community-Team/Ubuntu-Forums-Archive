---
title: "partition flag error on installing ubuntu"
date: 2006-09-11
forum: Installation &amp; Upgrades
---

### Post by gfwp on 2006-09-11
Hello,

I've found a BAD error on the installation mechanism:

If you install Ubuntu as sole OS, the partitioning program will NOT SET THE 
BOOT FLAG "on" on the booting HD.

This is not a big problem for new computers, but for old machines... well the BIOS will give some problems and finally the boot is not possible. So after installation you'll have an error from BIOS after rebooting, and everythings stops.

The BIOS doesn't allow GRUB to start his job.

To fix this just boot with the liveCD, then with parted set the "boot" flag to "on" and reboot from HD.

gfwp

---

