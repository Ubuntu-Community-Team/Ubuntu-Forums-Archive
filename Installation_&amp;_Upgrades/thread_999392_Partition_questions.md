---
title: "Partition questions"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by nickski on 2008-12-01
I have a question about my harddrive partition.  I partitioned my disk about half for vista and half ubuntu.  I'm getting sick of running stuff that gives me a bsod in windows so i am planning on just using it for games.  I want to give most of my hd to ubuntu, but i'm afraid if i re-partition it, it might screw up the start up files.  Is this what the [recovered] choice in the boot menu is for?  Any help to ease my fears would be appreciated...

(the only reason i ask because i remember hardy does not have any recovery files on the boot cd, but i am using Intrepid now so i'm not sure if that has changed or not)

---

### Post by Partyboi2 on 2008-12-01
You should be able to use the resize tool in vista to resize down your vista partition to the size you want, then boot a ubuntu live cd and use gparted (System>Admin>Partition Editor) and resize ubuntu to use the newly unallocated space.

---

### Post by nickski on 2008-12-01
Yea but when you use gparted, i'm afraid it will mess up the start up files in ubuntu, and i don't want to go through that (again).  It has happened to me on a laptop and when i popped in the live cd it said it could not repair broken files.

---

### Post by forkandles on 2008-12-02
You could always try the "leave well alone" option.
Unless your Ubuntu half of the disk is very small, why bother?
Ubuntu does not need a fraction of the space that Vista requires.

If you MUST repartition then Partyboi2 is correct about the first bit, always use the Vista shrink tool to reduce the Vista partition to a minimum.
Partyboi2 may well be right about the second bit but I would be extremely cautious.

BACKUP everything first before you attempt it!

The way I would do it would be to use the Vista shrink , then create new partitions for Ubuntu in the remaining space using gparted Live, followed by a fresh install of Ubuntu into those partitions.
Then copy over your backed up data to the Ubuntu partitions.

Since you have Vista and Ubuntu running at the moment you obviously know all about running a maximum of 4 primary partitions. To get round this use 3 Primaries and a new Extended which includes several Logical partitions.
Grandmother and egg sucking, probably!
All the best.

---

### Post by vanadium on 2008-12-02
If you keep Windows on the machine, yu can just leave the partitioning as is, and use your Windows partition for data storage. You can create a convenient link in your home partition to your data on your Windows partition. That way, you have conveniently and transparantly (you are not really aware that you are working on a different partition) to your user files, without ever having to navigate through Windows system directories. If your ntfs volume needs to be checked or maintained, you have Windows to do that.

---

### Post by nickski on 2008-12-02
thanks everyone

oh yea i have another post about mythtv questions.  If any of you are fimiliar with mythtv please comment on my post...thanks for your help

---

