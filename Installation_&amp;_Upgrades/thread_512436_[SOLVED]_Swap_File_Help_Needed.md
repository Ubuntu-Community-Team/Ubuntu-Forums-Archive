---
title: "[SOLVED] Swap File Help Needed"
date: 2007-07-29
forum: Installation &amp; Upgrades
---

### Post by crjackson on 2007-07-29
I've been trying to get my storage system working correctly after adding a hard drive (replaced and IDE with an SATA and moved some things around (including the boot drive).  I THINK most things are working correctly now.

BUT is that bolded entry below supposed to be there.  It looks like I have an EXTRA partition identical to my swap fpartition.  Do I need this?  Is it safe to get rid of? 

Does it look like my swap file is working properly on sda5?

Thanks


charles@K8N-Neo4-Platinum-SLI:~$ sudo fdisk -l

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8289    66581361   83  Linux
**/dev/sda2            8290        9039     6024375    5  Extended**
/dev/sda5            8290        9039     6024343+  82  Linux swap / Solaris

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9039    72605736    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      484518   244197040+   7  HPFS/NTFS

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1      484520   244198048+   7  HPFS/NTFS
charles@K8N-Neo4-Platinum-SLI:~$

---

### Post by mikewhatever on 2007-07-29
You can read more about partition types here [http://www.ubuntu.com/aboutus/contactus](http://www.ubuntu.com/aboutus/contactus)
Your set up is perfectly fine, no need to worry or delete any thing.

---

### Post by crjackson on 2007-07-29
> **mikewhatever said:**
> You can read more about partition types here [http://www.ubuntu.com/aboutus/contactus](http://www.ubuntu.com/aboutus/contactus)
Your set up is perfectly fine, no need to worry or delete any thing.

Thank you for your assistance...

---

