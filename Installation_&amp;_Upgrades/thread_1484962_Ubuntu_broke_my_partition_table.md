---
title: "Ubuntu broke my partition table"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by Tom743 on 2010-05-16
I tried to install ubuntu 10.04, i got to the drive selection screen and it saw my drive as all unallocted space (it actually has 180gb windows, 30gb unallocted space then 20gb data partition) so i exited out of the install and into the live CD. I went to the built in partition manager in ubuntu and formatted the freespace as ext4 but it gave an error message. I then tried to boot back into Windows 7 but it said no boot device available.

So at the moment my drive is like 180gb unallocted space, 30gb priamary ext4 with notthing on it, 20gb unallocted space.

The unallocated space should be Windows 7 and Data. Is there any way to fix this without losing data? I have access to CMD on the Windows recovery CD and terminal on the Ubuntu live CD.

---

### Post by srs5694 on 2010-05-16
My suspicion is that you've damaged your boot loader in the Master Boot Record (MBR; the first sector of the hard disk); however, your description of what you've done is extremely imprecise. For more precision, I suggest you start by posting the output of "sudo fdisk -lu" when typed at a command prompt in Ubuntu or an emergency disc (such as [PartedMagic](http://partedmagic.com)). Please add "[noparse]```
[/noparse]" to the start and "[noparse]
```[/noparse]" to the end of the fdisk output; this will preserve its formatting and improve its legibility.

FWIW, the original problem was most likely caused by a minor error in the partition table, as described [here.](http://www.rodsbooks.com/missing-parts/index.html)

---

### Post by John Bean on 2010-05-16
> **srs5694 said:**
> FWIW, the original problem was most likely caused by a minor error in the partition table, as described [here.]("http://www.rodsbooks.com/missing-parts/index.html")

Interesting. I had exactly the same symptoms described by the OP when attempting to install one of the late Lucid RCs. I fixed the damage very easily (and without data loss) using testdisk and waited for the real release - which I'm pleased to report installed without incident.

It would be nice to know the cause so as to avoid it in future - it happened at a stage before the installer had any business writing to the disk - but I'm not losing any sleep over it.

---

