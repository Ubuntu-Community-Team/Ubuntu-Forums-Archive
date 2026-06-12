---
title: "Two Ubuntu OS = Two GRUB's?"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by etyrmi on 2010-03-17
I multiboot Karmic, Win7 & Ubuntustudio 9.10, and everything works like a charm.

After my installation of Studio on sda8, however, GRUB seems to read the grub.cfg file from Studio instead of my regular Ubuntu partition. The problems with this are-

1. Grub does not update automatically when new kernels are added, and in fact does not find the latest Kernel at all.
2. Impossible to delete my installation of Studio without making my computer unbootable.

Just to be clear, the regular Karmic distro is my main OS, so I want GRUB to be read from my sda3 partition.

So do I have 2 GRUBS installed, one on each of my Ubuntu distros? And how do I get my mysterious bootable sda1 to point to the right one? (My boot partition is created by Win7, and seems to contain only windows files).

All help is greatly appreciated!

//////////////////////////////

fdisk list here>

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd4e377e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26        6297    50369257+   7  HPFS/NTFS
/dev/sda3            6298       16495    81915435   83  Linux
/dev/sda4           16496       38913   180072585    5  Extended
/dev/sda5           16496       17103     4883728+  82  Linux swap / Solaris
/dev/sda6           17104       29852   102406311    b  W95 FAT32
/dev/sda7           36196       38913    21832303+  83  Linux
/dev/sda8           29853       36195    50950116   83  Linux

---

### Post by zvacet on 2010-03-17
I don´t believe that you have two grub-s installed.More likely you installed Ubuntu studio last and that put it grub to MBR overriding previous one.You can easily change that if you reinstall grub fron your Karmic live CD following [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by psusi on 2010-03-17
Yep, you have two grubs installed.  To get back to using the Ubuntu one, boot into Ubuntu and run sudo grub-setup '(hd0)'

---

### Post by etyrmi on 2010-03-17
I booted the live CD

In terminal:
sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Which I got from this thread:
[http://ubuntuforums.org/showthread.php?t=1395592](http://ubuntuforums.org/showthread.php?t=1395592)

And it worked.

Thanks a lot guys, I love this forum.

---

