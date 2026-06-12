---
title: "Cannot write partition"
date: 2005-06-01
forum: Installation &amp; Upgrades
---

### Post by @ngelot on 2005-06-01
When I'm trying to manually format a free part (80GB) of my second HD as ext3 with Ubuntu Install (i386) I get an error message saying that it can't write to partitiontable - giving me the option Go back and Continue.....

With Go back the computer halts and I have to reboot to get the prosess started again....

BTW: Running Win XP SP2 on my first HD. Having all my files on the first part of my second HD (80GB). The rest of my second HD are empty (no filesystem - free space) and here I would like to put Ubuntu...

What can I do - please help!

@ngelot

---

### Post by mingus on 2005-06-01
What did you use to create hdb1, and what is its filesystem?

---

### Post by @ngelot on 2005-06-02
[QUOTE=mingus]What did you use to create hdb1, and what is its filesystem?[/QUOTE]It's NTFS and I think I either made it with XP or PartitionMagic...

@ngelot

---

### Post by BeeZ on 2005-06-02
[QUOTE=@ngelot]It's NTFS and I think I either made it with XP or PartitionMagic...

@ngelot[/QUOTE]
 try typex?

---

### Post by mingus on 2005-06-02
First, you need to consult the manual:

[http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch03s05.html](http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch03s05.html)

[http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch06s03.html#di-partition](http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch06s03.html#di-partition)

The installer will use the default PartMan program to create the partition.  You have the option of using an alternate partitioner, see:

[http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/apbs05.html](http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/apbs05.html)

PartMan is supposed to be able to handle NTFS partitions.  However, there are differences between how file systems, operating systems, and even partitioning tools calculate drive geometries and write the partition table.  This is why it is strongly advised to partition with a tool native to the OS being installed, and to not mix partitioning tools.

My experience with ParitionMagic and Linux partitioners has been OK, but there are known issues using the Windows Disk Manager and other partitioners.

If you have PartitionMagic, you can create your Ubuntu partitions in advance.  The manual has recommended partitioning schemes.  Be sure to also create the swap partition.  And, if you want to be able to write to the NTFS data on hdb1, you can use PM to convert it to FAT32.

Do not bother to format them, as the Ubuntu installer will want to do that.

If you do not have PM, or as an alternative, you can try cfdisk instead of PartMan, as described in the above manual.

Of course, it is critical that your hdb1 data be backed up before doing *anything* that affects the partition table.

---

### Post by alastair on 2005-06-02
Try going to a shell (ALT+F2?).

Then listing the disk partitions e.g.

fdisk -l /dev/hda
fdisk -l /dev/hdb

---

