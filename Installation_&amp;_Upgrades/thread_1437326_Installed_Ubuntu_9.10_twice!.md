---
title: "Installed Ubuntu 9.10 twice!"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by asookazian on 2010-03-23
So I have at least two new partitions with Ubuntu 9.10 installed on both (the first ISO/disk was corrupted and the 2nd one I tested first then installed).

So what should I do?  How can I view the partition info and delete the 1st install/partition as I'm assuming it's taking up unnecessary space on the hard disk.  thx.

---

### Post by l.billon on 2010-03-23
Hi!
Gparted is a software which efficiently deletes and creates new partitions.

---

### Post by asookazian on 2010-03-24
I'm guessing backup to external hard disk and then use fdisk or parted utilities to remove the extra partition?

But how do I know which partition is being used when I restart my machine and select one of the Ubuntu versions on startup?

---

### Post by cottfcfan on 2010-03-24
Boot into the one that works, go into system/administration/system monitor, then select file systems, it will tell you which partition you are using, then just use Gparted to delete the other one.
 Just make sure your good partition is the one that handles grub.
It will do if it was the last one you installed.

---

