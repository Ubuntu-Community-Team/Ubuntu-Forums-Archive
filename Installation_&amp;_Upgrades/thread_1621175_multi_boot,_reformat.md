---
title: "multi boot, reformat"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by pjmlmas on 2010-11-13
Hi:

I currently have the following:
1 primary partition xp/ntfs
1 extended partition
..logical fat partition for data
..logical ext4 ubuntu#1 10.04
..logical ext4 ubuntu#2 10.04

I want a boot partition for grub. I want to reformat hard drive as well.

Would I be able to make partition backups of xp, ubuntu#1 and ubuntu#2 partition and restore to newly formatted hd?
As long as I recreate partitions on reformatted hd same size, s/b ok?

So I could have
1 primary boot grub partition, correct? What filesystem type?
followed by
1 primary partition xp/ntfs?
1 Extended partition
(dont care about fat partition size)
Thee two ubuntu logical partitions?

---

### Post by cybergnome on 2010-11-14
I don't know what you mean by "boot partition".  Booting from a partition, rather than the MBR, is know to be problematic.  You would need to eliminate the XP boot code in the MBR.  And if formatting the disk is important, then a clean reinstall of all OSes is probably better than trying to backup and restore.

FWIW, I would non-destructively repartition XP, moving data with a third party Windows partitioner, rather than try to backup and restore it to another partition.  What do you intend to gain from this?

---

### Post by pjmlmas on 2010-11-14
i want to have grub installed in its own "partition". it is being clobbered by windows program.

i also was under the impression that a "partition" for grub is less problematic and recommended.

> 
You can, however, load all of Grub into your /boot partition. This saves the need to meddle with any of the data stored at the beginning of the disk. By default the code in the MBR will find the active partition and transfer control to the first sector of that partition. 

So I would still boot to MBR, but the grub code would be in its own partition, outside of the MBR. MBR just calls the active partition.

That is the reason for the change. I am having multiple issues with grub. Was hoping putting it in its own partition would help.

[http://ubuntuforums.org/showthread.php?t=1610327]("http://ubuntuforums.org/showthread.php?t=1610327")

Any insight appreciated.

---

### Post by bradbury on 2010-11-14
I ran into a problem using Grub2 (in 10.10) when I had 2 hard drives in the machine.  Apparently the mapping of the A & B drives may be different in Grub 2 vs. Grub 1.  I think what happened was it got into a mode where it thought the B drive was the A drive and couldn't find any of the partitions by the uuid specification.

I finally worked around it by simply unplugging the power from the B drive.

As long as you are creating partitions of the same size you can easily do things like "dd if=/dev/sda2 of=/dev/sdb2 bs=32k" (read the man page on dd before using).  Then fsck the "of" partition, mount it and see if it looks ok, repeat for as many partitions as you want.  What you cannot do is expand/shrink the partition size using "dd".  For that you have to use mkfs on sdb# and do a cpio, typically something like "cd /sda-dir/top-dir; find . -depth -print | cpio -pdamu /sdb-dir/mnt-point" (with the file systems fully mounted and much slower because it has to read and recreate the file system).

Be *very* careful doing this (esp. the dd) option -- get a single letter wrong and you could easily lose data.

I run grub on a separate /boot partition, typically /dev/sd[ab]3, with sd[ab]1/2 being the Windows Primary/Restore partitions.  My root, user, home partitions typically start at sd[ab]5/6/7 with a swap partition thrown in someplace in the middle (so it is between the root and user file systems).

But I've also run grub off of the MBR and the /boot directory as part of the root partition without problems.  Before going to all the trouble outlined above I'd suggest looking at diagnosing the Grub 2 problems (Ubuntu shot itself with the "lets make things more complex gun" with that one) and possibly falling back to Grub 1 which seems to be much simpler.  I've built and installed Grub 1 directly from the sources (not the Ubuntu binaries) and it isn't too difficult.

---

