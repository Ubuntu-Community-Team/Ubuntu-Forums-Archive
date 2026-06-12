---
title: "Installer crashes at partition screen"
date: 2018-06-14
forum: Installation &amp; Upgrades
---

### Post by leif-s-o on 2018-06-14
Hello!

This happens both with version 16.04 and 18.04. I bought a Windows laptop (Lenovo V330) and want to install Ubuntu. I created a live USB and the live system works. When I try to install Ubuntu, there is screen where you choose the partition. There are no partitions shown though, and when I click "+" or "-", the wizard just freezes and crashes a little later.

I would be thankful for every help!

---

### Post by yancek on 2018-06-15
The most common reason for this problems is having windows 8/10 installed and leavaing fastboot and/or hibernation on.  Turn those off and then use windows Disk Management to shrink your largest windows partition to leave free/unallocated space on the drive on which to install Ubuntu.  If you have a new laptop, I supposed it has windows 10 so I would also suggest that you read through the Ubuntu documentation at the link below before beginning your install.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by leif-s-o on 2018-06-17
Thank you! I solved the problem now in a different way: I set the SATA controller in the BIOS to AHCI, that made it work.

---

