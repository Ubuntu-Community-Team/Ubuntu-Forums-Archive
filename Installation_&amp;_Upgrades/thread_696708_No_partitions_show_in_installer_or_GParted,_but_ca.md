---
title: "No partitions show in installer or GParted, but can mount them"
date: 2008-02-14
forum: Installation &amp; Upgrades
---

### Post by jonty-comp on 2008-02-14
I was silly enough to partition my new 500GB SATA hard drive using PartitionMagic in Windows, and now when I try to install Ubuntu from the latest LiveCD it's partitioner shows the whole disk as unallocated.  This is annoying because I intentionally set aside 100GB for Ubuntu to reside in, with 100GB for Windows and the rest for both!

Strangely FDisk can see my partitions and make changes to them, and I can mount them all using the normal methods.  I have also tried the alternate install CD, that doesn't show them either.

Is there any other way I can get it installed on the partition I set aside?  I formatted it as ext3 in PartitionMagic, and Terminal as well, and I can write files to it.

Help is appreciated! :)

---

### Post by taurus on 2008-02-14
There is gparted, System -> Administration, on the LiveCD so why don't you use that to format that space to ext3 first.

---

### Post by jonty-comp on 2008-02-14
Sorry, I should have explained that, GParted is what the installer partitioner uses, isn't it? GParted shows my entire disk as unallocated too.

---

