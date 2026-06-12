---
title: "Help with dual-boot installation"
date: 2006-06-22
forum: Installation &amp; Upgrades
---

### Post by Albi on 2006-06-22
Hi,
I made a 15gb partition from my NTFS Windows XP hard disk with PartitionMagic and formatted it into FAT32, but whenever I try to install ubuntu to this drive, it says
"error: no root filesystem".
Now, PartitionMagic recommends a LinuxExt2 or LinuxExt3 format for installing Linux.  Will formatting the partition into any of these two filesystems work or is there something else I have to do to make it work?

---

### Post by aysiu on 2006-06-22
Ubuntu will automatically reformat into Ext3 any drive you specify to reformat. The error about "no root filesystem" means you haven't specified a mount point for /

/ is the root filesystem under which all the other folders in the filesystem live.

It's kind of like C:\ in Windows.

[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html) may help you.

---

