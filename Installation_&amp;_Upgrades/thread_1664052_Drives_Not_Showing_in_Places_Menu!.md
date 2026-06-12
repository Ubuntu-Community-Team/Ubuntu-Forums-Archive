---
title: "Drives Not Showing in Places Menu!?"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by 99digit on 2011-01-10
this is my fdisk -l

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2434    19549805   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2            2434       19457   136738145+   f  W95 Ext'd (LBA)
/dev/sda3   *        2678       11043    67199863+   7  HPFS/NTFS
/dev/sda5            2434        2677     1952768   82  Linux swap / Solaris
/dev/sda6           11044       19457    67585423+   7  HPFS/NTFS

but i cannot see the NTFS drives in the Places Menu. Previously they appeared in the Places menu like Places -> New Volume and Places -> New Volume_

What can be done to get them back? what commands?
Also when I plugin the USB it does not get auto mounted like it use to before.

[NOTE: i had tried to install Windows and messed up the grub, which i could fix and load Ubuntu following the instructions on Ubuntu site itself. I have deleted Windows now though.]

[Solved]NTFS configuration tool did it

---

