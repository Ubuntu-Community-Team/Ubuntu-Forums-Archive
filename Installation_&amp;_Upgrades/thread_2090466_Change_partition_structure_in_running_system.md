---
title: "Change partition structure in running system"
date: 2012-12-02
forum: Installation &amp; Upgrades
---

### Post by nafihsus on 2012-12-02
I am running a dual-boot system with Win7 and Ubuntu (10.04), currently not sharing any data between the two. I'd like to switch to a structure with separate partitions for each OS (as small as possible, as big as necessary) and data in a third partition that can be accessed by the other two.

I wonder whether it is possible to get there without reinstalling the OS.
Attached is a hardcopy of the current partition structure from GParted.

---

### Post by Bucky Ball on 2012-12-02
The newer versions of Windows must have their partitions shrunk with Windows software. *_Do not_* attempt to do this with Gparted in Ubuntu. 

To expand/shrink partitions otherwise they need to be unmounted and therefore you need to run from a LiveCD, the install CD, and unmount them (as you can't unmount the Ubuntu partition while your running Ubuntu on it, naturally). 

Open Gparted when booted from the LiveCD, right click and unmount the Ubuntu / partition then shrink. I never use anything over 15Gb for a Ubuntu install myself and have symlinks to folders on my data partition inside the /home folder on / rather than the *actual* folders. Symlinks are very easy to create (basically shortcuts to the real stuff).

Your data partition should be NTFS for Windows and Ubuntu to be able to read/write to it. Hope that helps some ... ;)

---

### Post by darkod on 2012-12-02
To add to the above, I have to notice that you don't have too much unused space to consider repartitioning. But it depends on the type of data filling the partitions.
For example, sda2, your windows partition, is almost full 100% and that's very bad for windows. You do need to create some free space there. But if it's full of OS files and programs, you can't easily move them to another partition without reinstalling the programs.
On the other hand, if the data there is mostly photos, videos, etc, you can easily move them to another shared ntfs partition and use them from both OSs. You would still need to move them temporarily to external storage, shrink sda2, and then creating the shared ntfs partition and move them back there.

Depending whether you plan to shrink the /home partition too, that might be little bit complicated. You have to watch out about shrinking logical partitions and the extended partition container.

And you have to plan first in advance what to shrink and from which end, because you need the unpartitioned space to be joined into one big unpartitioned space so you can create one big ntfs partition.

For example, if you shrink sda2 by moving the start of the partition, the unpartitioned space will end up between sda1 and sda2, so you can't join it with any unpartitioned space you create from the linux partitions because they are after sda2.

And before starting any partitioning, make sure you have a full backup of all your important data because operations like this one can go wrong sometimes losing your data.

---

### Post by nafihsus on 2012-12-03
Thanks for the hints. sda2 contains Win7 and all related data, which I will backup first. Then I will try to split sda2 into two partitions one for the remaining OS the remainder for what should be used for Ubuntu, which I plan to reinstall.

The current sda4/5/6/7 I will try to combine to one data partition (NTFS).  

Hope I'll get to that between Christmas and New Year.

---

### Post by oldfred on 2012-12-03
You still have to stay within the rules of 4 primary partitions, with one primary allowed to be converted to an extended partition and then the extended can hold many logical partitions. So most of your new/changed partitions should be planned as logicals.

---

### Post by Mark Phelps on 2012-12-03
> **nafihsus said:**
> Thanks for the hints. sda2 contains Win7 and all related data, which I will backup first. Then I will try to split sda2 into two partitions one for the remaining OS the remainder for what should be used for Ubuntu, which I plan to reinstall.
You basically can NOT do that.  Why? Because you already have three primary and one extended partition.  IF you shrink sda2 and then FORCE the creation of another partition in Win7 Disk Management, it will convert your partitions to Dynamic Disks -- something you do NOT want to do.

> The current sda4/5/6/7 I will try to combine to one data partition (NTFS).
They're already ALL inside a single Extended partition -- so that won't give you the ability to create another partition in and of itself.

---

