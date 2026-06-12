---
title: "Any advanges to using a logical partition?"
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by MasterNetra on 2008-10-29
I was wondering if there are any advanges and/or disavanges to using Ubuntu on a logical partition?

---

### Post by Partyboi2 on 2008-10-29
There is no disadvantage to my knowledge of having ubuntu on a logical partition. You can only have 4 primary partitions, so having a extended partitions with logical partitions can be very useful if you are dual or triple booting.

---

### Post by MasterNetra on 2008-10-29
What really is the real difference between a primary and a logical? And does Ubuntu perform better on either or is there really no difference to Ubuntu?

---

### Post by Kobalt on 2008-10-29
From the Arch wiki : 

> Primary partitions can be bootable, and are limited to 4. If a partitioning scheme requires more than 4 partitions, we are forced to use an extended partition which will contain logical partitions.

Extended partitions are not usable by themselves; they are merely a "container" for logical partitions. If required, a hard disk shall contain only one extended partition; which shall then be sub-divided into logical partitions.

When partitioning a disk, one can observe this numbering scheme by creating primary partitions sda1-3 followed by creating an extended partition, sda4, and subsequently creating logical partition(s) within the extended partition; sda5, sda6, and so on. 

---

### Post by fendres on 2008-10-29
There should be no difference in anything, except for machines with a very old BIOS.

---

### Post by MasterNetra on 2008-10-29
Ah so it doesn't matter at all i guess. Thanks all.

---

### Post by Partyboi2 on 2008-10-29
> **MasterNetra said:**
> Ah so it doesn't matter at all i guess. Thanks all.
No, only if you are running out of primary partitions :p

---

### Post by Rocket2DMn on 2008-10-29
I tend to prefer primary partitions because they are bootable and sometimes easier to manage.  One disadvantage to keeping logical partitions around when you don't need them is that you cannot expand a physical partition into a logical partition space.  So say if you have an extended partition with a few logical ones inside.  You delete the first logical one (at the front of the extended partition) - now in order to expand the physical partition that touches this area, you have to first shrink the extended partition before you can grow the physical partition into the newly emptied space.  This leaves more opportunity for a failure to occur (though unlikely, it is still possible - resizing partitions is perhaps the most dangerous operating when it comes to fiddling with partitions).

Details, but hey, you asked.

---

### Post by Shazaam on 2008-10-29
Since I have two hard drives I have made only two "main" partitions. One drive is devoted totally to a primary partition for WinXP. The other has one Extended partition taking up the whole drive (except for a small section of unpartitioned space) with multiple logical partitions inside. Boots/runs fine with no problems. sda is an SATA drive, sdb is a PATA (IDE) drive and the pc boots from the sata (grub is on the sata)....
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00047d37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38626   310263313+   5  Extended
/dev/sda5               1         781     6273319+  82  Linux swap / Solaris
/dev/sda6             782        3350    20635461   83  Linux
/dev/sda7            3351        8471    41134401   83  Linux
/dev/sda8            8472       13648    41584221   83  Linux
/dev/sda9   *       13649       26567   103771836   83  Linux
/dev/sda10          26568       29256    21599361   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000096f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    7  HPFS/NTFS

```

---

