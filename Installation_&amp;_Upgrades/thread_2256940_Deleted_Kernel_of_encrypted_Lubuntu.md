---
title: "Deleted Kernel of encrypted Lubuntu"
date: 2014-12-15
forum: Installation &amp; Upgrades
---

### Post by ngr27 on 2014-12-15
I needed some space in /boot to update my computer, and instead of doing it properly, I removed all of my kernels. Now when I restart my computer it goes straight to memtest86.

I'm attempting to follow the instructions here ([https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels/Problems](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels/Problems)) to recover. Here's where I'm at:
```
lubuntu@lubuntu:~$ sudo -i
root@lubuntu:~# fdisk -l

Disk /dev/loop0: 638.2 MiB, 669229056 bytes, 1307088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00030caa

Device     Boot  Start       End   Sectors   Size Id Type
/dev/sda1  *      2048    499711    497664   243M 83 Linux
/dev/sda2       501758 625141759 624640002 297.9G  5 Extended
/dev/sda5       501760 625141759 624640000 297.9G 83 Linux

Disk /dev/zram0: 1010.5 MiB, 1059528704 bytes, 258674 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk /dev/zram1: 1010.5 MiB, 1059528704 bytes, 258674 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
root@lubuntu:~# mount /dev/sda1 /mnt
root@lubuntu:~# for fs in sys proc dev dev/pts; do mount /$fs /mnt/$fs; done
mount:  /sys is not a block device
mount:  /proc is not a block device
mount:  /dev is not a block device
mount:  /dev/pts is not a block device
root@lubuntu:~# 

```

I did a lot of internet searching, and I know that I am certianly not the first person to have found myself in this situation. However, I have yet to find an example of someone who is doing this with an encrypted HDD (such as the one that Lubuntu lets you set up on installation). I'm assuming that **sda1** is correct, but just by going off of the linked instructions this not clear to me. Also, note that when I try to prep to change roots, I get the "/sys is not a block device" message. I'm not really sure what to makeof that. I've been working on this problem for almost three days now before coming here, but I'm really out of my depth on this one and need some help. Thanks!

---

