---
title: "Ubuntu 7.04 Crash"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by shack1069 on 2007-06-12
I have a crash problem with Ubuntu 7.04. My computer has a 40 GB hdd with 10 GB each 4 partitions. The first is a primary disk, all others are logical disks.

I had this disk configuration: 

- A primary partition NTFS and other three are logical partitions. I had allotted the third logical partition to Ubuntu by making it a free space from within WinXp during Ubuntu installation. The partitions C: (1), D: (2), and F:(4) were NTFS. The third partition was allocated to Ubuntu and Ubuntu had installed itself using the automated disk partitioning. It created one swap partition and the other large ext3 partition for programs and data.

C:  Primary (NTFS) WindowsXp  (Partition -1)
D: Logical disk (NTFS)  (Partition - 2)
455 MB Swap Ubuntu partition (Automatic) (Partition - 3)
9.5 GB ext3 partition
F: Logical disk (NTFS)  (Partition - 4)

I accidently deleted the Ubuntu swap partition from within WinXp. Now I cannot boot my system. Grub gives an error 122 message. Plus, I cannot access my fourth NTFS partition. Windows show a total of 3 partitions, two NTFS (C & D) and one large 19 GB free space. I have lost my valuable data on fourth NTFS partition.

What should I do? Help me please. I am completely new to Linux and Ubuntu.

Shack

---

