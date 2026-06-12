---
title: "Uninstalling for another run at it!"
date: 2006-10-16
forum: Installation &amp; Upgrades
---

### Post by starbase1 on 2006-10-16
Hi All,
I transferred Ubuntu from the live CD onto a partition on my hard disk, which sort of worked - but now I'd like to remove it for a clean start all over again.

I tried using Partition Magic under windows to clear the partition it was using, but it said it could not get access.

Is there an option within Ubuntu itself to uninstall, and remove it from the multi boot startup?

Nick

---

### Post by ajgreeny on 2006-10-16
I've never used Partition Magic so can't help with that but suggest the live CD of Gparted.  Google for it and download, it's only a 25MB iso.
If you want to uninstall and immediately reinstall ubuntu you will not need to do anything except install again in the same partitions.
If you are dual booting and want to change the partition arrangement, you will need to change the windows partition first, eg make it smaller or whatever, using the manual partitioner in the install ubuntu setup (defrag first).
If you just want to run windows for a while, you will need to repair your master boot record with the windows install CD, as ubuntu will have put grub onto the MBR in place of the windows MBR.
The simplest will be to just reinstall ubuntu as you had it before, and overwrite the existing partitions on the hard disk, but there may be other reasons for changing things, such as the need to enlarge the ubuntu partition so you will need to make sure you get it right this time before you jump in.

---

### Post by starbase1 on 2006-10-16
Thanks, that sounds like its worth a go!

---

### Post by gn2 on 2006-10-17
> **starbase1 said:**
> Thanks, that sounds like its worth a go!

Be very careful, if you've got Partition Magic DEFINITELY use it instead of gparted.

All you need to do is delete the Ubuntu partition and it will be gone.

You can then create a new partition in the vacated space.

You might want to remove Grub, but if you do you will have to run "fixmbr" from Recovery Console on the Windows install CD

---

### Post by jhenager on 2006-10-17
You also can use aefdisk, which fits on a floppy.
[http://www.aefdisk.com/](http://www.aefdisk.com/)

As always, back up critical data before messing with partitions.

---

