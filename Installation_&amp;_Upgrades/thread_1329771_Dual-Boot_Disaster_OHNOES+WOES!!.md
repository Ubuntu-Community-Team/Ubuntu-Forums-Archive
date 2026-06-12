---
title: "Dual-Boot Disaster? OHNOES+WOES!!"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by istigkeit on 2009-11-17
I am trying to set up a dual Windows-Ubuntu boot, but seem to have run into a bit of a problem. I've done a little searching and research, but can't seem to find what I need to take care of this, so hopefully someone can provide me some help or point me in the right direction. Thanks to everyone in advance.

I have a regular C: drive with my normal XP install.

I also have G: drive which is an external USB hard drive. This has no operating system, just backup files. I chose to install Ubuntu here.

I did the regular side-by-side install from my live cd and it seemed to go smoothly. I was prompted that the install was successful and I re-booted.

While booting, I only get a "File not Found" message and a "rescue grub" prompt.

From here, I don't know what to do.

This is what I get if I do sudo fdisk -l

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18e918e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xacdd9b22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       72584   583030948+   7  HPFS/NTFS
/dev/sdb2           72585       77825    42098332+   5  Extended
/dev/sdb5           72585       77639    40604256   83  Linux
/dev/sdb6           77640       77825     1494013+  82  Linux swap / Solaris

```From what I can tell it is installed and all my files are intact.

What have I done wrong?

---

### Post by mikewhatever on 2009-11-17
Grub in Karmic is rather new so let's learn together. Can you navigate to your Ubuntu partition and post the contents of the following file:

/boot/grub/grub.cfg

Don't modify it, cause we don't want more mess then there is already.

did you have an older version of Ubuntu installed before?

---

### Post by istigkeit on 2009-11-18
It appears that file contains nothing but a plain text file named grubenv

---

