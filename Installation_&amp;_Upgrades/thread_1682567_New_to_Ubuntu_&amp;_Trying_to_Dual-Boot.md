---
title: "New to Ubuntu &amp; Trying to Dual-Boot"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by BreakItLikeItsHot on 2011-02-06
Hello everyone!

First off, I'd like to say that I'm more or less new to Linux, except for having it used several time on rootservers (without gui). Since I have a chunk about 50 GB free on my disk, I decided that it would be a good moment to get Ubuntu. 

First I partitioned the space to a NTFS drive (since I'm using W7) and wanted to use Wubi, which failed me by giving an error during the download, due to that I'm now downloading the iso manually and I will try to make Wubi use it (If that is possible).

As I expect it to not work the way I want, I would be prepared to delete the NTFS drive I have created and install Ubuntu Manually on the free space. Since I already read, that various users are reporting problems and confusions with the installer, I want to go do it in Advanced mode.

This is how my partitioning looks like atm:

[IMG]http://www.abload.de/img/unbenanntl9u1.png[/IMG]
The first one is a Primary partition that used to hold Windows Vista, It's the one Windows 7 accesses to boot.
The Second one listed is the free space which I could use for Ubuntu.
The third is my Data partition.
The fourth is my Windows 7 partition.
The last is some random partition that has no purpose other than annoy me and It cannot be deleted for whatever reason.

Now I was planning to create 3 new partitions with Ubuntu
/ - With 15GB
swap - With 4096MB (as much ram as I have)
/home - with the rest (about 30 GB)

Now my question, will I run into any problems? Should I do something differently?
I heard something about that you can only have 4 partitions, which would mean that I wouldn't be able to install ubuntu... <.<

I can't delete the first partition, since It would mean a complete reinstall of windows and I don't want to.

Thanks for the help.

EDIT: If I manage to install Ubuntu manually, could I still be able to dualboot? Or do I have to make special settings before being able?

---

### Post by Quackers on 2011-02-06
Welcome to UF.
Can I ask how your C:, E: and images partitions became Logical? Using Windows 7 they would normally all be primary partitions. Also, these logical partitions being present, I would expect an extended partition to be shown ( which is effectively a container for logical partitions), and there doesn't appear to be one.
Your imagen partition is likely to be some kind of backup image, for recovery purposes, and, as such, should not be deleted, unless you have made a set of recovery dvd's.

---

### Post by BreakItLikeItsHot on 2011-02-06
Thanks for the reply!
The E: Partition was logical since the dawn of time haha,
The C: partition is logical, because the primary OS of the computer used to be Vista and I had 7 alongside, until I switched to 7 and deleted Vista. 

I have no Idea about the extended partition though.

---

