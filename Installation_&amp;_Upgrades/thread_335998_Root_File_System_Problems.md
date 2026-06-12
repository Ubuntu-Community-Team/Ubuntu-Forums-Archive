---
title: "Root File System Problems"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by AgentSmith15 on 2007-01-11
I want to start learning more about linux so when I tried installing Ubuntu 6.10 I get a problem on step five of six. I can't press forward because I get a error message that says "No Root File System". I have a AMD 64 x2 with one hard drive with 4 partitions. Two of the partitions came with my laptop and the other two are the ones I made with acronis. I did fdisk and then tried mounting hda3 but I had no luck...

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         894       17237   131283180    7  HPFS/NTFS
/dev/hda2               1         893     7172991    b  W95 FAT32
/dev/hda3           17238       19326    16779892+  83  Linux
/dev/hda4           19327       19457     1052257+  82  Linux swap / Solaris

Partition table entries are not in disk order



Anyone know what I can do?

---

### Post by hal10000 on 2007-01-11
Which partitions were made by acronis?

Don't use acronis to create linux partitions, it's better to be made by linux itself.
Delete the two linux partitions (with acronis or another partition manager).

Then just boot your ubuntu cd and do the installation again.
When it asks for which partitions to be used by linux, then tell it to use the largest free space on the disk (i forgotten which step this is and how it is named).

This should fix your problem.

btw, the fdisk command says that the "Partition table entries are out of order", this is not really a bug, its just annoying, but you can't fix this by now because your windows sytem would then refuse to boot.

---

