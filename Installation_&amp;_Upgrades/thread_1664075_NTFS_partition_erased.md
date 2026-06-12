---
title: "NTFS partition erased"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by Cosmofan on 2011-01-10
I have eee pc with 2 partitions. Wanted to install Ubuntu on 2-nd logic disk. Created ext4 20 Gb partition on drive D and was expecting Ubuntu to keep my data on 2-nd NTFS partition. Did not make format. But remaining space turned into "not distributed". So the data is lost. How could I get my NTFS structure back if possible?

---

### Post by Mark Phelps on 2011-01-11
Anytime you clobber a drive partition, the only reliable way of recovering it involves removing it from the PC in question and hooking it up to another PC.  Why? Because every time you write to that partition, you seriously worsen your chances of not being able to recovery anything.

However, if you are able to boot into Ubuntu and want to get the NTFS partition back, you could try using Testdisk.  Some folks have reported good results doing this.

---

