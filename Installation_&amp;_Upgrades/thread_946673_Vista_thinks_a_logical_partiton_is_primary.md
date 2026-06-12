---
title: "Vista thinks a logical partiton is primary"
date: 2008-10-13
forum: Installation &amp; Upgrades
---

### Post by gregkarr on 2008-10-13
I trying to get a system working where I want to dual boot Vista and Ubuntu. The current issue I'm having though is that after shrinking the Vista partition to free up space I installed Ubuntu and created only a root partition and a swap partition. This was done using the manual option in the installation process. The idea was to create the swap partition as a logical partition, but when I open Vista's disk management tool it labels the swap partition as primary and complains that I have 4 primary partitions so I can't make any more. I have attached a screenshot from Gparted, and clearly there the swap partition was created within an extended partition (which means Gparted sees it as Logical right?). 

Finally, the reason I want to create my last partition in Vista and not in Gparted is to ensure Vista assigns it a drive letter in a correct way (had trouble with this before). The last partition I want to create I intend to be an NTFS partition that both Ubuntu and Vista can use to access my files, music, videos etc.

---

### Post by Pumalite on 2008-10-13
You can still use Gparted, make it Fat32. If you have problems with the size of the files; make it ntfs. Ubuntu comes with the ability to read and write to ntfs out of the box.

---

### Post by gregkarr on 2008-10-13
Thanks for the reply. So you're suggesting that I just use Gparted to create a FAT32 logical partition right? Will this show up in Vista though? Remember the problem is that Vista doesn't recognise the swap as a logical partition. Hence it thinks I have 4 primary ones and I'm wondering if it will be able to see beyond that? I mean, once you have 4 primary partitions you can't have any more.

---

### Post by Pumalite on 2008-10-13
If you want to dual boot Vista and Ubuntu in the same drive; you have to allocate space for Ubuntu with the Vista partitioner first. Then you can install Ubuntu in the freed space. I'd keep Ubuntu's home as storage and use this driver for Vista:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
You can create a Fat32 partition if you want, but keep in mind the 4 per drive rule (primary partitions)

---

