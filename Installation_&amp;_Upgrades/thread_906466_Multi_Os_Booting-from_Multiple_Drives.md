---
title: "Multi Os Booting-from Multiple Drives"
date: 2008-08-31
forum: Installation &amp; Upgrades
---

### Post by ronnie_147 on 2008-08-31
Hi All

I have got 3 hard disks (40,80 and 500 gb).I first installed Win XP on 500gb disk,and later i put ubuntu(8.04) on the 80gb one.
When i start the comp(booting from 80gb one),the Grub screen comes up with options of ubuntu and Win Xp,but the windows does not load.

I get Error 13:unexpected format something
The entries in menu.lst files are below:
## ## End Default Options ##

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=83a8d46b-a4b8-4fc0-8b52-f25fb4f2e927 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=83a8d46b-a4b8-4fc0-8b52-f25fb4f2e927 ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title Microsoft Windows XP Professional
root (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1


can someone help me in this.
cheers
shaq

---

### Post by cdtech on 2008-08-31
Could you post the output of:
sudo fdisk -l

Could be you need to modify the line:
root (hd2,0)
to:
rootnoverify (hd2,0)

---

### Post by ronnie_147 on 2008-08-31
thx for the reply.Here is the o/p of sudo fdisk -l command :


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x405e405d

Device Boot Start End Blocks Id System
/dev/sda1 * 1 9327 74919096 83 Linux
/dev/sda2 9328 9729 3229065 f W95 Ext'd (LBA)
/dev/sda5 9328 9729 3229033+ 82 Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008f250

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 4865 39078081 83 Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
102 heads, 51 sectors/track, 187768 cylinders
Units = cylinders of 5202 * 512 = 2663424 bytes
Disk identifier: 0x69205244

Device Boot Start End Blocks Id System
/dev/sdc1 * 1 6352 16521526+ 7 HPFS/NTFS
/dev/sdc2 6353 187767 471860415 f W95 Ext'd (LBA)
/dev/sdc5 6353 66824 157287646+ 7 HPFS/NTFS
/dev/sdc6 66825 127296 157287646+ 7 HPFS/NTFS
/dev/sdc7 127297 187767 157285045+ 7 HPFS/NTFS

---

### Post by cdtech on 2008-08-31
Yes I seen the sdc1 as your Windows drive (hd2) so the menu.lst is correct, you just need to modify it somewhat.

**Update::.**
Examples of the difference from the GNU/Linux and GRUB device names:

**1st Physical Hard Drive:**
Linux IDE: GRUB IDE: Linux SCSI: GRUB SCSI:
/dev/hda1 ----(hd0,0)----- /dev/sda1-------(hd0,0)
/dev/hda2 ----(hd0,1)----- /dev/sda2-------(hd0,1)
/dev/hda3 ----(hd0,2)----- /dev/sda1-------(hd0,2)
/dev/hda4 ----(hd0,3)------/dev/sda2-------(hd0,3)

**2nd Physical Hard Drive:**
Linux IDE: GRUB IDE: Linux SCSI: GRUB SCSI:
/dev/hdb1---- (hd1,0)----- /dev/sdb1------ (hd1,0)
/dev/hdb2---- (hd1,1)----- /dev/sdb2------ (hd1,1)
/dev/hdb3---- (hd1,2)----- /dev/sdb1------ (hd1,2)
/dev/hdb4---- (hd1,3)----- /dev/sdb2-------(hd1,3)

---

### Post by ronnie_147 on 2008-08-31
so you mean i need to change the partition location number in the list :
**root (hd2,0)**
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

or to 

**rootnoverify (hd2,0)**

---

### Post by ronnie_147 on 2008-09-01
hi..
         i tried changing **root (hd2,0)** to **rootnoverify (hd2,0)**,but didnt work.Also tried combinations with (**(hd2,0)** changing partition number,but still no results.
         Any idea what is wrong.The hard disk 2 entry looks correct.dont know why it is not booting.

thx

---

### Post by cdtech on 2008-09-01
This is the way I have mine set up (without the map):
```

title		Windows Vista
root		(**hd1**,0)
savedefault
chainloader	+1

```
Just change the drive to your (**hd2**,0)

---

### Post by manishtech on 2008-09-01
> **ronnie_147 said:**
> Hi All

I have got 3 hard disks (40,80 and 500 gb).I first installed Win XP on 500gb disk,and later i put ubuntu(8.04) on the 80gb one.
When i start the comp(booting from 80gb one),the Grub screen comes up with options of ubuntu and Win Xp,but the windows does not load.

I get Error 13:unexpected format something
The entries in menu.lst files are below:
## ## End Default Options ##

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=83a8d46b-a4b8-4fc0-8b52-f25fb4f2e927 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=83a8d46b-a4b8-4fc0-8b52-f25fb4f2e927 ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title Microsoft Windows XP Professional
root (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1


can someone help me in this.
cheers
shaq
AM a bit confused. As Windows is on 3rd hard disk then it means its hd2 and ubuntu on 1st hard disk so its hd0 . then why is this map statement there?

I am not able to understand that though the entires in GRUB are correct, why is this map statment there? Should'nt the map line be removed? # it out and then try.

---

### Post by ronnie_147 on 2008-09-01
i tried changing to rootnoverify (hd2,0).  with and w/o map statement,but again the same prob..
any further tricks

thx
shaq

---

### Post by gregphil on 2008-09-01
I just went through this and got it to work OK for me.
The really confusing thing is that Linux changes the names of the disks if you change the "boot order" in your BIOS setting.

So... you need to pick one BIOS setting and leave it alone while you are trying to get your GRUB menu worked out correctly.  I leave mine set to SATA boot.

I have Window Xp on the first IDE drive
Ubuntu 8.04.1 on the first SATA drive
Kubuntu 8.04.1 on the second SATA drive

If the BIOS boot order is set to IDE before SATA I get the Windows bootloader (from the mbr of the IDE disk) and no Linux options.

If the BIOS boot order is set to SCSI before IDE (ie SATA first) I get the GRUB menu fro the MBR of the first SATA drive.  In this case the options in GRUB allow selection of one of the three operating systems. The Windows option goes thru the normal Windows boot loader (is "chained")

My relevant GRUB menu.lst lines look like:

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3196e3f5-d538-4a64-aad8-b3eda368d85b ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3196e3f5-d538-4a64-aad8-b3eda368d85b ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Kubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8441227a-acd7-4bda-9aaa-d74251eee147 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot

title		Kubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8441227a-acd7-4bda-9aaa-d74251eee147 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot

title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

Note how the final entry needed to swap the drive mappings so Windows is booting from the "first" hard drive.

Hope this helped.

---

### Post by Herman on 2008-09-01
The 'map' commands are to trick Windows into thinking it is booting in a first hard drive so you won't need to edit boot.ini, so, if you know how to edit boot.ini to tell Windows what hard drive it's in, you can do without the 'map' commands. 
It's easier to use GRUB than to edit boot.ini though.

---

### Post by ronnie_147 on 2008-09-01
so finally solved the problem...my bios setting didnt reflect the drive order...so my 2nd drive was set to 40gb instead of sata 500gb...hence was unable to boot...
thx a ton to gregphil...i never gave a thought that BIOS setting was related to linux booting....
so now i can switch OS w/o having to change BIOS each time..
thx again

cheers
shaq

---

