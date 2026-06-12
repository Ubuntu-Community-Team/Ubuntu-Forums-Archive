---
title: "Ubuntu can't find hard drive at install"
date: 2011-06-07
forum: Installation &amp; Upgrades
---

### Post by slanger87 on 2011-06-07
I know there's another thread on this but nothing on that helped me. I live booted from cd and USB, I can go into GPART and see the the partitions, but when I go through the install process I can't select anywhere to install it. Below is the output of fdisk -lu. Also, I went into BIOS and changed the SATA setting to IDE and that didn't affect anything. I can post system information if that will help. Thanks in advance for any input.

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9a0d0322

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206911  1929586687   964689888+   7  HPFS/NTFS
/dev/sda3      1929586688  1953122303    11767808    7  HPFS/NTFS
```

---

### Post by Quackers on 2011-06-07
Welcome to UF :-)
Are you using a SATA3 port? Or a raid array? Is it a Mac?

---

