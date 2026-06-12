---
title: "Ubuntu 7.10does'nt find hd"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by sakkeclaque on 2008-02-24
Hello,
first of all i am a noob in linux..
here is something from my terminal, the first hd of 20 gig is found but the one of 80 gig isnt. Can someone help, please?
sander@sander-desktop:~$ sudo fdisk -l

Disk /dev/hda: 20.4 GB, 20404101120 bytes
255 heads, 63 sectors/track, 2480 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfb75fb75

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         547     4393746   83  Linux
/dev/hda2             548        2480    15526822+   f  W95 Ext'd (LBA)
/dev/hda5             638        2480    14803866    c  W95 FAT32 (LBA)
/dev/hda6             548         637      722862   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x21117c12

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9729    78148161    7  HPFS/NTFS
Note: sector size is 2048 (not 512)

Disk /dev/sda: 495 MB, 495321088 bytes
233 heads, 6 sectors/track, 173 cylinders
Units = cylinders of 1398 * 2048 = 2863104 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         173      483696    6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 6) logical=(0, 1, 1)

---

### Post by Pumalite on 2008-02-24
I see your 80 GB as hdb in your fdisk.

---

### Post by sakkeclaque on 2008-02-24
yess.. what does it mean??
(noob i know)

---

### Post by Pumalite on 2008-02-24
It's your 2nd drive in the system.

---

### Post by sakkeclaque on 2008-02-24
yes, but how do i get it in the menu "places" ?

---

### Post by Pumalite on 2008-02-24
Go to Applications>Terminal:
sudo mkdir /media/ntfs
sudo mount -t ntfs-3g /dev/sdb1 /media/ntfs
You have to have installed ntfs-3g:
sudo aptitude install ntfs-3g

---

