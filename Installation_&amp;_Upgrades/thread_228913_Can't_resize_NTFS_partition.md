---
title: "Can't resize NTFS partition"
date: 2006-08-03
forum: Installation &amp; Upgrades
---

### Post by niels on 2006-08-03
Hi there,

I'm doing a dual install on a laptop with Win XP on it. I would like to resize the big NTFS partition, so that there is 10 GB for Ubuntu. But when I try to do the resizing, GParted tells me, that it can't resize/move the partition. What's the problem???

The harddisk have the following partitions:
Partition, Filesystem, Size, Used, Flags
/dev/hda1, ntfs, 48.83 GB, 15.09 GB, boot
unallocated, unallocated, 7.84 MB, --, --
/dev/hda2, fat32, 6.04 GB, --, --, lba
/dev/hda3, ntfs, 1.00 GB, 609.70 MB, --

Hope anyone is able to give an answer...

---

### Post by halfvolle melk on 2006-08-03
NTFS support isn't so hot on linux. You might want to try and resize it from Windows with Partition Magic.

---

### Post by Jagot on 2006-08-03
Defragment the hard disk then try and resize it again.

---

### Post by mdelorme on 2006-08-04
Yeah, if you have a look at [http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php), you'll notice that gparted supports ntfs shrinking, but not moving.  This implies that if you are trying to create space before the ntfs partition by shrinking it, it will likely cause a failure (since this involves moving the head of the partition).  For windows partitions, partition magic's the way to go.  For linux partitions, steer clear of partition magic and use gparted.

---

### Post by graabein on 2006-08-04
I want to partition a NTFS harddrive and I have Partition Magic. I have defragmented the entire drive and when I resize the partition -- the only partition on the hd -- I get a "pending action" message after. When I hit "apply" I get a popup that says something about unknown boot point or something similar. I have cancelled this because I don't want to make a mistake.

I dual boot Dapper with XP and use Grub as boot manager. The drive I want to partition contains just one big Windows partition so I figure I resize it and create a Linux partition from the free space with GParted afterwards.

Any pointers?

---

### Post by seafever on 2006-08-04
we can't setting ntfs in linux system

---

