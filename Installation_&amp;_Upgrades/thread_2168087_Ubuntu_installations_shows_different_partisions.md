---
title: "Ubuntu installations shows different partisions"
date: 2013-08-16
forum: Installation &amp; Upgrades
---

### Post by srivastava4aeveryone on 2013-08-16
Hello,

I am trying to install Ubuntu along with Windows 8.

I have choose to create partitions during installation

The problem is the Ubuntu installation shows different partitions when compared to partitions which I see in windows explorer.

I could not understand the reason and really appreciate any help to solve this issue.

---

### Post by grahammechanical on 2013-08-16
Based upon what I have read in posts on this forum it is always best when we have Windows installed to create space for ubuntu using Windows Utilities. First defrag the hard disk more than once. Make sure Windows can load. Resize the Windows partitions and make sure Windows can load And then try to install Ubuntu using the Something Else option to install Ubuntu into the space created.

Windows and Linux view things differently. This is to be expected and they name things differently. Windows will call partitions "drives" and label them with letters. In Linux a hard disk is "sda" = first sata drive. A second hard disk would be "sdb" = second sata drive. Partitions are given a number. So, sda1 = first partition on first sata or (a) drive. and sda6 would be partition 6 on the first sata or (a) drive.

Regards.

---

