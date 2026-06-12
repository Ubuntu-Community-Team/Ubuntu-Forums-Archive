---
title: "Grub points to wrong partition"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by tokyoscoop on 2008-03-30
OK, I've been going around in circles on this and I'm sure it's an easy problem to fix. I have a Lenovo laptop with Windows XP on one partition and the recovery image on another. Ubuntu is installed on a USB HDD.

Grub offers a choice of OS but selecting Windows always ends up with the recovery system starting (which doesn't let me do much).

Running fdisk -l it looks like the bootable partition points to the recovery partition (sda2) and not the main Windows one (sda1). How do I repoint this? Seems like such an easy thing but it's been driving me nuts for hours.


Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10243    77437048+   7  HPFS/NTFS
/dev/sda2   *       10244       10337      710640   1c  Hidden W95 FAT32 (LBA)

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa1beb3c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       13995   112414806   83  Linux
/dev/sdb2           13996       14593     4803435    5  Extended
/dev/sdb5           13996       14593     4803403+  82  Linux swap / Solaris

---

### Post by housam on 2008-03-30
Edit you Grub page ```
gksudo gedit /media/boot/grub/menu.lst

```
then change the the (red 1 to 0 ) as follows :
```
title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,[COLOR="Red"]1[/COLOR])
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```

to be  :
```
title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,[COLOR="red"]0[/COLOR])
kernel      /vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro quiet splash
initrd       /initrd.img-2.6.20-15-generic
quiet
savedefault
```

---

