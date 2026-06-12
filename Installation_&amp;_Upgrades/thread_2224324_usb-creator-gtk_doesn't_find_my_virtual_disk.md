---
title: "usb-creator-gtk doesn't find my virtual disk"
date: 2014-05-15
forum: Installation &amp; Upgrades
---

### Post by Grozoeuf on 2014-05-15
Hi,
I know how to create an USB to install linux. I've done it.
But now I'd like to do some tests with usb-creator. And instead of making useless writings onto my USB stick, I wanted to make an installation on a "virtual disk-partition".
The trouble is that : when I launch usb-creator-gtk, it finds my /dev/sdb2 (REAL usb formated into Fat32) but NOT any virtual disk. And I have no idea why.
If you can help, it'd be very cool :)

(I think that my post doesn't fit well with this part of forum, so, sorry, but I really didn't know where to put it :()

here is what I did :

```
     
     mkdir /tmp/t7; cd /tmp/t7
     dd if=/dev/null of=vu7 bs=1 seek=3800M count=0
     losetup /dev/loop7 vu7
     sfdisk -uM /dev/loop7 << EOF
     > 10,3000,c,*
     > ;
     > EOF

     fdisk -l /dev/loop7
     # Device Boot      Start         End      Blocks   Id  System
     # /dev/loop7p1   *       16065     6168959     3076447+   c  W95 FAT32 (LBA)
     # /dev/loop7p2               1       16064        8032   83  Linux

     mknod /dev/loop7p1 b 7 8
     losetup /dev/loop7p1 -o $((512 * 16065)) --sizelimit $(((6168959-16065)*512)) vu7
     mkfs.vfat -F 32 /dev/loop7p1
     # --> mkfs.fat 3.0.26 (2014-03-07)
     # --> Loop device does not match a floppy size, using default hd params

     install-mbr /dev/loop7
     partprobe /dev/loop7
     partprobe /dev/loop7p1 

```
but in the end usb-creator-gtk completly ignores my loop7p1 device

---

