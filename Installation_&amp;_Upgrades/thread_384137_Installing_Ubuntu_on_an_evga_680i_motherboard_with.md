---
title: "Installing Ubuntu on an evga 680i motherboard with RAID enabled"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by some.hacker on 2007-03-14
Ubuntu 6.10 Edgy "Alternate"

I have an evga 680i motherboard, and I multiboot Ubuntu and Windows XP. The Windows Partition shares a Hard drive with the Linux Partitions. I also have a RAID-0 array which I must have access to. Right now, the RAID array is plugged into SATA ports 0 & 1, and the windows/linux hard drive is in port 2. The only way I have gotten Windows XP to work so far is to  unplug the RAID array when installing and running Ubuntu. If I attempt to boot to Ubuntu when the array is plugged in, grub fails to find the partition the kernel is installed in, however Windows boots just fine. If I try to install Ubuntu with the RAID array plugged in, nothing boots. Who else is having this problem out there? Has anyone found a solution?

---

