---
title: "need help with dual booting"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by dayfall on 2007-05-25
i know there are a bunch of "howto"s and tutorials but none of them could help me with my specific configuration. besides, they are all very long and complicated and i miss the point somewhere in the middle every time.
what i'm looking for is a simple step by step guide on installing ubuntu on my system. if anyone can provide such help, it would be highly appreciated.
i have two hard drives, one has a primary NTFS partition with windows xp pro installed. the second one is still unallocated, and i would like to have ubuntu installed on it. so what i need to know is:


**how exactly should i partition the drive?** (file system, primary/logical)


**and how can i install ubuntu on that second drive, so when i turn on my computer, i would get to choose which operating system to boot?** (with a default OS and a timer of course)


_**thank you very much in advance!**_

---

### Post by confused57 on 2007-05-25
Since you have 2 hard drives, you might want to consider this method:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

With the above method, you wouldn't be installing grub to your Window's drive mbr & you can boot Windows from grub on your Ubuntu drive.
You can have a maximum of 4 primary partitions on a hard drive, however one of the primary partitions can be an extended partition that can contain as many logical partitions as you want or need.  The Ubuntu default install(use entire disk) is root as a primary partition, formatted as ext3 filesystem type...swap is a logical partition(one extended partition is created).  You might want to create a separate home partition, format as ext3...see the guide below.

Have you seen this guide for installing with the desktop live cd?:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by dayfall on 2007-05-25
first of all, thank you for the exceptionally quick reply and the good will.
i read both of the links you posted, and as a newb with linux, i found the second tutorial of much use.
i'm currently backing up my files, after which i will reformat my windows partition, set up windows then linux on the second drive
thank you very much :KS

---

