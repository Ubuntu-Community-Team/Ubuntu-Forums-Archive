---
title: "Flexible Partitioning Tool"
date: 2013-09-21
forum: Installation &amp; Upgrades
---

### Post by noorez on 2013-09-21
I have been away from the ubuntu scene for a while...

When I installed ubuntu, I used the text partitioner to set up lvm partitioning the way that I wanted. However, ubuntu does not have the text installer with the desktop image anymore. Is there a partitioning tool with the flexibility of the old text based one that I could use during/before installation? 

I don't minding playing around with manual lvm stuff however the tool did provide convenience with the encryption setup.

---

### Post by Bashing-om on 2013-09-21
noorez; Hi !

What about "fdisk" ?
see:
```

man fdisk

```
> 
 fdisk  (in the first form of invocation) is a menu-driven program for creation
       and manipulation of  partition  tables.   It  understands  DOS-type  partition
       tables and BSD- or SUN-type disklabels.


[INDENT][INDENT]Hey, it is one way to do
[/INDENT][/INDENT]

---

### Post by 1clue on 2013-09-21
Don't use fdisk.

Fdisk only understands MS-DOS partition tables.

MS-DOS partition tables became obsolete when hard drives exceeded 32 megabytes.  I've been using it up until I got my current setup.

The whole partition table in the free space at the end of the MSDOS boot loader was a dirty hack to cope with HDD bigger than 32Mb (yes Megabytes) 
The extended partition was another dirty hack to cope with HDD > 128Mb. (still Mb).

MS-DOS partition tables have been hacked to the point where they can understand up to 2T disks.  My desktop has 5 disks in it, 4 of which are more than 2T.  The other one is an ssd.


Use parted and a GPT partition table.  Or search on gpt in the repository.  Gdisk is also there but not really useful for anything complicated.

---

### Post by noorez on 2013-09-22
Okay, update: I installed ubuntu encrypted following this guide: [https://wiki.archlinux.org/index.php/Encrypted_LVM](https://wiki.archlinux.org/index.php/Encrypted_LVM)  luks on lvm section. 

The only thing that hurts me now is configuring grub and initramfs. The guide only appears to work with ArchLinux. How can I make it work for ubuntu? Right now I cannot boot into my install. I however can manipulate with with a live cd and chroot environment.

---

### Post by noorez on 2013-09-23
Okay. Solved...

It seems the only thing I had to do was correctly create the /etc/crypttab file and rebuild the initramfs.

---

