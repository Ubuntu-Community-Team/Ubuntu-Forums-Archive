---
title: "Installation problems - disk alignment offset"
date: 2014-04-12
forum: Installation &amp; Upgrades
---

### Post by Gabry_van_Winden on 2014-04-12
When installing ubuntu on my laptop I get a warning that indicates the  partition is misaligned by 3584 bytes. I have consulted various topics  on adjusting the partition alignment, all to no avail. I have succeeded  in moving the starting point of the partition to various points, 512  bytes, 2048 bytes, 4096 bytes. on each occasion I still get the same  message indicating the same value, 3584 bytes. 

This is what my fdisk -l reports looks like:

Disk /dev/sda: 30.2 GB, 30198980608 bytes
255 heads, 63 sectors/track, 3671 cylinders, total 58982384 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Alignment offset: 3584 bytes
Disk identifier: 0x0008c10f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            4096    58982383    29489144   83  Linux
Partition 1 does not start on physical sector boundary.



I  am getting the impression that the real problem is the offset of the  disk itself, but I have no clue as of how to fix this. If anyone can  help me out it would be greatly appreciated.

---

### Post by tgalati4 on 2014-04-12
That is an old disk.  What is the make and model?  Perhaps it has a security/encryption feature that needs a special driver.

Rather than fight it, create a small first partition of 100 MB, then install on your second partition.  *gparted* will usually come up with a warning that your partition does not end on a physical sector boundary and ask you if you want to correct it.

If you don't want to waste the space on the first partition, install [TinyCore]("http://www.tinycorelinux.net/install.html") as a backup.

---

### Post by Gabry_van_Winden on 2014-04-16
Thanks for your response, I will try this out tonight.

---

### Post by Gabry_van_Winden on 2014-04-16
I have created a first partition of 100mb as you advised, yet now I get the message during installation that the partition starts at an offset of 3072 bytes from the minimum alignmend of this disk. 

The disk is a ATA SW80MSAMCN-32-G, I hope this helps.

---

### Post by Gabry_van_Winden on 2014-04-26
Bump.

Is there anyone out there who can help me? Do you need further details on my device and configuration?

---

### Post by Luke M on 2014-04-26
This may be informative:

[http://www.novell.com/support/kb/doc.php?id=7007193](http://www.novell.com/support/kb/doc.php?id=7007193)

> 
There's one special case: When internal 4k block sizes were introduced, some HDD manufacturers actually addressed the classical DOS partition table misalignment by shifting the logical sector counting by one, so a start at sector 63 would translate to sector 64 (i.e. internal block 8). Some HDDs even were configurable with a switch to do this shifting by one. The SATA spec did even provide a mechanism for the drives to report such an offset, so the OS can take the appropriate steps to optimize performance. To our knowledge not many such drives exist; and only a subset of them reports the offset correctly. 

 

What OS did this machine originally come with?

---

