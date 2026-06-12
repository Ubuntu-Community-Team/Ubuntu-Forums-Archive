---
title: "Problems installing a external USB Drive"
date: 2007-08-12
forum: Installation &amp; Upgrades
---

### Post by Amof on 2007-08-12
Hello,

After searching for forum posts on this problem I kept getting referred to this forum so here I am! I’ve been a Linux user since I was 15 year of age and I’ve gone though many distros. Of course, Ubuntu us by far the best.

Anyway, I have just purchased a Free Agent 230 GB USB external drive for use on my Ubuntu computer. It’s formatted in NTFS but I have the app needed to read and write on it. The problem I have is that I have a PCI SCSI controller in my computer which runs 2 SCSI Drives. When I plug in the USB drive and restart Linux it will assign the USB drive as my “sda” which normally contains my filesystem I.E. root.   This kinda stinks because when I try to boot, it says it fails to boot my filesystem.

So I guess my question is there any way to manually define how Ubuntu maps this drive? I tried doing this using the fstab but to no avail. 

Thanks in advance!

---

