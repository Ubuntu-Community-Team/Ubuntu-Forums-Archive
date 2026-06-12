---
title: "Install Ubuntu Gutsy to external hard drive."
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by indianballer24 on 2007-12-20
I want to install Ubuntu Gutsy on an external hard drive. 

1. Is there any way I can partition my external hard drive. (It is 500 GB and I only want to use 100 GB for my installation). 

2. If I do partition it will I still be able to use the remaining 400 GB for storing other files. 

3. Is it possible to install Grub on a flash drive so I can set my bios to boot from the flash drive and then load ubuntu from my hard drive?

Please give step by step instructions. Any help is greatly appreciated.

---

### Post by logos34 on 2007-12-20
1. Use Gparted (system>admin>gnome part editor) on the gutsy live cd.  You can have up to four primary partitions, or 3 primaries and an extended, which can further be subdivided into many logical partitions 
2. yes. in any filesystem type.
3. Why not just install grub to MBR of the 500gb drive and boot directly from that? See [this thread (post #502)]("http://ubuntuforums.org/showthread.php?t=80811")

---

### Post by indianballer24 on 2007-12-20
> **logos34 said:**
> 1. Use Gparted (system>admin>gnome part editor) on the gutsy live cd.  You can have up to four primary partitions, or 3 primaries and an extended, which can further be subdivided into many logical partitions 
2. yes. in any filesystem type.
3. Why not just install grub to MBR of the 500gb drive and boot directly from that? See [this thread (post #502)]("http://ubuntuforums.org/showthread.php?t=80811")

What exactly is the difference between an extended partition and a primary partition? And will I still be able to access the hard drive for data storage if I install grub to its MBR.

---

### Post by logos34 on 2007-12-21
> **indianballer24 said:**
> What exactly is the difference between an extended partition and a primary partition?

google the disk partitioning wiki

>  And will I still be able to access the hard drive for data storage if I install grub to its MBR.

yes

---

