---
title: "partition manager"
date: 2005-06-29
forum: Installation &amp; Upgrades
---

### Post by marc777 on 2005-06-29
Hello,

I'm trying to install ubuntu on a P233 with two disks of 2GB.
But every time I reach the partition manager saying
"checking disks"  it doesn't go further than 41 %
Is there a way to solve this problem and continuing installing?

Marc (HOLLAND)

---

### Post by remin8 on 2005-06-29
Sounds like you have a bad drive. I would just go to ebay and get a new/used drive on the cheap. Or run ubuntu live! :)

---

### Post by mingus on 2005-06-29
[QUOTE=marc777]Hello,

I'm trying to install ubuntu on a P233 with two disks of 2GB.
But every time I reach the partition manager saying
"checking disks"  it doesn't go further than 41 %
Is there a way to solve this problem and continuing installing?

Marc (HOLLAND)[/QUOTE]

One possibility is that there are bad sectors on the disk.  With Windows, chkdsk /r will flag these sectors to not be used.  On Linux, the equivalent is e2fsck -c.  However, both these tools assume there is a filesystem already on the disk.  The only tool I know of (I'm sure there must be others) that does true "low-level" sector repair is Spinrite.

FWIF, I have a P133 with a 80GB disk.  The BIOS only supports 8.4GB, but Linux doesn't care because it doesn't get drive info from the BIOS and it doesn't care about geometries.

It may also be that you do not have enough RAM.  Another distro I installed failed for the same reason yours did - so I partitioned the disk with Knoppix and added a swap.  The installation kernel activated it and that fixed the problem.  I can't say if this would apply with Ubuntu.

---

### Post by marc777 on 2005-06-30
I've checked the disk wich took a very long while
after starting installation I decided to wait a long while again at the partitionmanager part  and indeed I could continue !!

Thanxs!

---

