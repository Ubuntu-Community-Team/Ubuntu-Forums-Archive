---
title: "Partition MAJOR screw up"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by audiphile on 2009-12-08
So I dont know what I'm doing, obviously. I reinstalled Ubuntu over another Ubuntu install because the nVidia flicker prevented me from logging on (and I didn't have the skill to troubleshoot in Linux)...

anyway, here is what I'm working with now. Any way to correct this issue or do I need to re-install everything? If reinstalling, how do I make sure I don't do this again?

thanks in advance!

&#65279;Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9442    75842833+   7  HPFS/NTFS
/dev/sda2           11404       12161     6085800   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3            9443       11403    15751732+   5  Extended
/dev/sda5            9443       11315    15044841   83  Linux
/dev/sda6           11316       11403      706828+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by darkod on 2009-12-09
> **audiphile said:**
> So I dont know what I'm doing, obviously. I reinstalled Ubuntu over another Ubuntu install because the nVidia flicker prevented me from logging on (and I didn't have the skill to troubleshoot in Linux)...

anyway, here is what I'm working with now. Any way to correct this issue or do I need to re-install everything? If reinstalling, how do I make sure I don't do this again?

thanks in advance!

&#65279;Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9442    75842833+   7  HPFS/NTFS
/dev/sda2           11404       12161     6085800   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3            9443       11403    15751732+   5  Extended
/dev/sda5            9443       11315    15044841   83  Linux
/dev/sda6           11316       11403      706828+  82  Linux swap / Solaris

Partition table entries are not in disk order

There are few thing that ideally shouldn't be there but nothing to prevent you from working. Do you actually have problems on the computer or you think your partitions are messed up? From this data it's not such a mess.

---

