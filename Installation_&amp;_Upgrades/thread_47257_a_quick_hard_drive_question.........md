---
title: "a quick hard drive question........"
date: 2005-07-07
forum: Installation &amp; Upgrades
---

### Post by cwncool on 2005-07-07
I have 2 hard drives one has XP installed on it and i want to install ubuntu on my second.  I was wondering, during the ubuntu install process, does it give you a choice of which drive to partition and install it on? Thanx!

---

### Post by mingus on 2005-07-07
Yes.  You can take two paths:  The "guided" partitioning, or "manual" control.  With either, you will be presented with a recommendation to be approved before rewriting the partition table.  I would add that, since there are many boot config alternatives when using 2 drives, when you get to the boot loader install step, it is best to say [no] to the automatic default which will take you to a screen where you can explicitly state where you want to loader to go.  If you intend to control the boot each time from a BIOS menu (some BIOS's offer this) or you intend to dual-boot from the Linux grub loader, then you will probably want to install grub to the second drive's MBR, usually /dev/hdb.  It is important to synchronize the grub install with the BIOS boot sequence.

---

