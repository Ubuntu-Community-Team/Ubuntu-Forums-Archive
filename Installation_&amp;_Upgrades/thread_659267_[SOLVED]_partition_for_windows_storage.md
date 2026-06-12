---
title: "[SOLVED] partition for windows storage"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by O||y on 2008-01-05
Hi.  I need more storage for my windows but I don't know how to nick some space from Ubuntu.

I currently have 3 250 gig hard disks.  First one is partitioned 3 ways, 10 gig for windows, then rest in 2 other partitions for windows programs and pics/music etc.  I have another 250GB hard disk for windows to use for storage also, being installed games and movies etc.  The third 250GB hard disk is where I installed Ubuntu.  It consists of the following according to GParted:

/dev/sdc

^ name of disk

/dev/sdc1 (has a padlock symbol) and is filesystem ext3 and is 222.69GiB in size.
/dev/sdc2 is extended
     /dev/sdc5 - the linux-swap, about 2 GiB

My question is this: How do I steal 200GB of space from sdc1 and partition it so that windows can use it in NTFS storage? - (I need it for storing some large files)

I don't know what I would have to do - would I format the hard disk to NTFS and create a small partition for ubuntu to live in (I don't m,ind starting from scratch with Ubuntu as I have nothing on here that can't be redone)  or would it be simpler - make partitions smaller to get some free space?

I am totally new to this, so any help will be greatly appreciated!!  I am afraid I am a n00b though, so please be quite explicit with instruction LOL

Thanks in advance,

O||y

---

### Post by logos34 on 2008-01-05
> **O||y said:**
> How do I steal 200GB of space from sdc1 and partition it so that windows can use it in NTFS storage?

Use Gparted on the live cd to shrink root sdc1 and create a new ntfs partiton (sdc3) in freed space

system>admin>gnome part. editor

if you also want to mount it in linux:
[https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971)

---

### Post by O||y on 2008-01-06
Thank you very much for your help.  I have now sorted my hard disk out.  I didn't think of running the livecd, but this now makes perfect sense as without a physical disk mounted, it is free to alter it!

Excellent advice - thank you!  =D>

---

### Post by logos34 on 2008-01-06
ok, wonderful.  Go to thread tools menu and mark as 'solved.'

---

