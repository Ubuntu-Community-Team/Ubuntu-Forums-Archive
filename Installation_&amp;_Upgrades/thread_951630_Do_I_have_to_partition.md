---
title: "Do I have to partition?"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by ShoeSh1ne on 2008-10-18
Might be a silly question, but I want to clarify it first:

I have 2 separate HDD, C and D.  On C I have XP and D is totally empty and I won't ever have to use it.  So my question is, can I just install Ubuntu on D and not worry about partitioning and dual-boot that way?

Thank you.

---

### Post by mikewhatever on 2008-10-18
By totally empty, you probably mean NTFS or FAT32 file system, and no files. That's good for installing Windows, but not Linux, so, yes, unless I am wrong and you simply call a bunch of unallocated space D, you have to partition.
That said, there is a way to avoid partitioning, by installing inside the NTFS partition. The program that makes it possible is called Wubi, and it's an option on the Desktop cd since Ubuntu 8.04.

---

### Post by JasenGroves on 2008-10-18
Even if you have two physical drives, you should do the partition. You probably won't have to, but it's something you should do.

But you don't have to. When installing, you first chose the hard disk you're instlaling it on, and your next choice would be to erase that disk and allow the installation to automatically partition for you.

[you can read about it here.]("https://help.ubuntu.com/community/GraphicalInstall#Select%20a%20Disk")

---

### Post by sandy8925 on 2008-10-18
hey when u mean u have two hdd's C and D do you meant to say that you have two hard disks or just two partitions on the same hard disk.

Anyway if D is a partition and  is completely empty then you don't need to partition.
Just format D to ext2 or ext3 using the livecd and then install ubuntu to that partition.

---

### Post by ShoeSh1ne on 2008-10-18
> **sandy8925 said:**
> hey when u mean u have two hdd's C and D do you meant to say that you have two hard disks or just two partitions on the same hard disk.


Two hard disks.

---

### Post by ShoeSh1ne on 2008-10-18
Well after getting it installed, I have been unsuccessful in getting it to recognize my wireless network.

I searched and searched and was unable to solve the problem.

Probably user error, but for someone wanting to give Linux shot, maybe making it a little more user friendly would help.  My little suggestion.

Or I just suck.

---

