---
title: "Error 12: Invalid device requested"
date: 2007-01-30
forum: Installation &amp; Upgrades
---

### Post by harun on 2007-01-30
Have a computer where my hard drive had two partitions. I first ran Win2k on the one partition and later installed XP on the second partition and used that. I destroyed the first partition and installed Ubuntu. Booting now, grub lets me go to Ubuntu just fine. I can see all the data on the other partition (the XP one) and would like to also boot XP. Here is the dump of menu.lst and below that the fdisk info. I get the error in the title of this post when I select the "Windows" option. I would like to know if there is anything I can try to get XP to boot. I tried a number of different things with SuperGrub and all came back with errors.

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet
boot

title           Microsoft Windows
rootnoverify    (hd0,4)
savedefault
makeactive
chainloader     +1


Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6395    51367806   83  Linux
/dev/hda2            7013        9728    21816270    f  W95 Ext'd (LBA)
/dev/hda3            6396        7012     4956052+  82  Linux swap / Solaris
/dev/hda5            7013        9728    21816238+   7  HPFS/NTFS

Partition table entries are not in disk order

---

### Post by zeeform on 2007-02-16
Hi did you ever solve this problem as i have exactly the same thing happening

---

### Post by harun on 2007-02-16
> **zeeform said:**
> Hi did you ever solve this problem as i have exactly the same thing happening


No. I decided to wipe the whole thing. Now I only run Ubuntu and no Windows.

---

### Post by trunks14 on 2007-07-14
I have Exactly the same problem, if it can't be solved at least make this a global warning as many people fall in this mistake :(, apparently caused from not having windows in (hd0,0).

Does any guru know why this is happening?

---

### Post by breker on 2007-07-24
I fixed this by changing the partition number [hd (0,0) > hd (0,3) to pick up the Windows partition.  Works fine now.l

---

### Post by Albundy213 on 2007-12-14
I'm having the same problem as well. But don't know what to do.

---

### Post by Albundy213 on 2007-12-14
I just realized this post doesn't start of with my question, maybe this is why I haven't received a response. I'm making a new post, hopefully that works

---

