---
title: "Recent update lost 2 hard drives..."
date: 2007-07-14
forum: Installation &amp; Upgrades
---

### Post by cwestpha on 2007-07-14
When i first installed 7.04 I had full access to all four of my internal hard drives (all SATA). When I applied the updates after a freash re-install I lost access to two of my hard drives.
I have an ICH 9R chipset with 4 hard drives. All set non-legacy to enable advanced features.
my current fstab-l reads:
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29651   238171626   83  Linux
/dev/sda2           29652       30401     6024375    5  Extended
/dev/sda5           29652       30401     6024343+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30402   244196352    7  HPFS/NTFS

```

/dev/sdc1 and /dev/sdd1 are missing (both are NTFS formated). I thought it was a problem with NTFS-3G support but clearly the system isnt even seeing them.
Before the updates I was able to see them just fine, after applying all of the updates I am unable to see the last two (both 200 GB seagates).
Both disks are accessible if I boot using an install CD/DVD.

In my search for a fix here I saw the winmac_fstab (uses the old read only mounting system) script and tried to run it. For the first half an hour to an hour the script wiil mount the system correctly and then eventually will fail saying its not found. I looked at the system logs and I don't see read errors.

---

