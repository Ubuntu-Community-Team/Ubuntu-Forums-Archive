---
title: "install ubuntu with win XP"
date: 2005-04-29
forum: Installation &amp; Upgrades
---

### Post by nancy25dec on 2005-04-29
Hi,

I've got win xp on my primary partion and want to install linux on my logical partion, but when i try to install it in my d: it gives file system error message can someone please help me in installing ubuntu. I'm installing linux for the first time.

---

### Post by Juergen on 2005-04-29
If you can see the partition as d:, it is already formatted with a windows-filesystem.

For a Linux-install you need free space, so just kill this partition in windows and try again (obviously move all data somewhere else before you kill it ;-)).
The setup should then create and format new partitions as it needs them.

If you want to share files between Linux and Windows, you should create a (small) FAT-partition, because that's what both can read and write.
You might want to do this in Windows before you start installing - but remember: leave the space after this FAT-partition unpartitioned.

---

### Post by derrick1985 on 2005-04-29
[QUOTE=Juergen]If you can see the partition as d:, it is already formatted with a windows-filesystem.

For a Linux-install you need free space, so just kill this partition in windows and try again (obviously move all data somewhere else before you kill it ;-)).
The setup should then create and format new partitions as it needs them.

If you want to share files between Linux and Windows, you should create a (small) FAT-partition, because that's what both can read and write.
You might want to do this in Windows before you start installing - but remember: leave the space after this FAT-partition unpartitioned.[/QUOTE]

To "expand" on what was just said:

Linux requires unalocated space, as in, non formatted space on the HD. Linux uses its own format for storing files called Ext3. Windows, can't format Ext3 (why would it).  Before you resize your partition, you should backup in Windows any essential files (documents, etc). Then, you would go into the Ubuntu installer, and when it starts up the paritioner, you could take the unallocated space and format it as Ext3 and be done with it. Linux would format it's partition over no problem.

If you want a GUI way of doing it, try System Rescue CD. [http://www.sysresccd.org/](http://www.sysresccd.org/)

The part about the fat partition:

Linux can READ (or see) the contents of an NTFS partition, but it cannon WRITE (or save) to it. So, if you want to share files between Linux and Windows (say you need to work on a document on both Linux and Windows) then you need something that the both of them can read/write to. A FAT32 partition both Linux and Windows can read and write to. So, if you want to do that route, you will also need to create yet another partition, formatted fat32.

Best of luck, any other problems just shout.

---

