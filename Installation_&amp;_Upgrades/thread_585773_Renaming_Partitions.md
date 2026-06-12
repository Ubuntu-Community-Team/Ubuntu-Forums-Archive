---
title: "Renaming Partitions"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by vmoros on 2007-10-21
Hi guys,

I installed Gutsy Gibbon and it's awesome. Everything works perfectly but in the installation process, My partitions' names got messed up so this is the order:
sda3
sda2
sda4

Is there anyway I can rename these partitions to be in the correct numerical order?

---

### Post by Pumalite on 2007-10-21
Post:
sudo fdisk -lu

---

### Post by vmoros on 2007-10-21
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe18240a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *   194579280   232685459    19053090   83  Linux
/dev/sda3              63   194579279    97289608+   7  HPFS/NTFS
/dev/sda4       232685460   234436544      875542+   5  Extended
/dev/sda5       232685523   234436544      875511   82  Linux swap / Solaris
Partition table entries are not in disk order

That's the output of sudo fdisk -lu.

---

### Post by Pumalite on 2007-10-21
You are fine.

---

