---
title: "Too many partitions on HDD"
date: 2015-11-03
forum: Installation &amp; Upgrades
---

### Post by ampage2 on 2015-11-03
Hello everyone, I am in the process of installing Ubuntu but the entire HDD is filled with partitions. Is there any way to figure out which partitions can safely be deleted? I don't care about the recovery partitions as I have a recovery disk that works fine so I will delete them as long as it is safe. I opened gparted but I'm pretty confused at what I'm looking at. There is also a 16GB SSD at /dev/sdb which is where I presume the OS itself is actually installed. Can I delete all of the partitions other than sdb5?

---

### Post by SeijiSensei on 2015-11-03
Rather than deleting partitions, I'd use the Windows disk manager (Control Panel > Computer Management > Disk Management)  to shrink the Windows partition then give the newly freed space to Linux during installation.

GParted can shrink Windows partitions as well, but I always prefer to use native Windows utilities when doing these kinds of low-level tasks.

---

### Post by yancek on 2015-11-03
There's no reason to delete anything, just do as suggested above and shrink the large windows partition to make room for Ubuntu.  Some of the other partitions could be boot and/or EFI partitions and a recovery CD generally will boot and access the recovery partition on disk to set to factory defaults.  So unless you backed up the entire system somewhere, your recovery disk will be useless without the recovery partition.

---

### Post by Bucky Ball on 2015-11-04
Agree with the above, shrink the Windows partition, but do NOT use Gparted. Boot to Windows and use its disk management software to shrink it.

(Please attach large screenshots by 'Go Advanced' or 'Adv Reply' and using the paperclip icon. Thanks.)

---

