---
title: "FC5/XP/ubutu multi boot problem with grub"
date: 2006-08-15
forum: Installation &amp; Upgrades
---

### Post by shadowspawn on 2006-08-15
Having been using FC5 for a couple of months after getting tired of XP not working in random ways I though that I would try a different Distro to see which suits me best.

I installed UBUNTU to a seperate HD that I have added to the PC and when complete nothing would boot - I was getting a Grub error 15 - Found out how to resolve this from the forum - FC rescue and reinstall grub.

Problem is now I can load XP and FC5 but no options for UBUNTU on the Grub menu - so I copied the entris the ubuntu install created on the new boot partition into the grub install that works,

Next I worked out that the drive mappings needed amending and trial and error seem to idicate that hd(3,0) works so
[HTML]title Fedora Core (2.6.16-1.2133_FC5)
	root (hd0,0)
	kernel /vmlinuz-2.6.16-1.2133_FC5 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.16-1.2133_FC5.img

title		Ubuntu, kernel 2.6.15-26-386
root		(hd2,0)
kernel		/vmlinuz-2.6.15-26-386 root=/dev/hdg5 ro quiet splash
initrd		/initrd.img-2.6.15-26-386
savedefault
boot[/HTML]  

Becomes 
[HTML]title Fedora Core (2.6.16-1.2133_FC5)
	root (hd0,0)
	kernel /vmlinuz-2.6.16-1.2133_FC5 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.16-1.2133_FC5.img

title		Ubuntu, kernel 2.6.15-26-386
root		(hd3,0)
kernel		/vmlinuz-2.6.15-26-386 root=/dev/hdg5 ro quiet splash
initrd		/initrd.img-2.6.15-26-386
savedefault
boot[/HTML] 

This triggers the ubuntu to load but it fails to mount the root drive.

Below is fdisk output for my PC.
Fc boot is on /dev/hda1
ubuntu boot is on /dev/hdg1
while the ubuntu / should be /dev/hdg5

[PHP]Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          13      104391   83  Linux
/dev/hda2              14         701     5526360   8e  Linux LVM
/dev/hda3   *         702        7033    50861758+   7  HPFS/NTFS
/dev/hda4            7034       14946    63561172+   f  W95 Ext'd (LBA)
/dev/hda5            7034       11885    38973658+   b  W95 FAT32
/dev/hda6           11886       12913     8257378+   b  W95 FAT32
/dev/hda7           12914       13234     2578401    b  W95 FAT32
/dev/hda8           13235       14053     6578586    b  W95 FAT32
/dev/hda9           14054       14117      514048+   7  HPFS/NTFS
/dev/hda10          14118       14946     6658911    b  W95 FAT32

Disk /dev/hde: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1               1        3738    30025453+  83  Linux

Disk /dev/hdg: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1               1         280     2249068+  83  Linux
/dev/hdg2             281         358      626535   82  Linux swap / Solaris
/dev/hdg3             359        1980    13028715   83  Linux
/dev/hdg4            1981       10011    64509007+   5  Extended
/dev/hdg5            1981        4582    20900533+  83  Linux
/dev/hdg6            4583       10011    43608411    b  W95 FAT32

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            6376       19457   105081133+   7  HPFS/NTFS
/dev/sda2   *           1        6375    51207156   8e  Linux LVM

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            6376       19457   105081133+   7  HPFS/NTFS
/dev/sdb2   *           1        6375    51207156   8e  Linux LVM

Partition table entries are not in disk order[/PHP]


Can anyone assist in getting to the last peice of the puzzlel for me? and complete the editing of GRUB so that the I can choose which OS to boot into properly.

on one of the other posts of this nature there was reference to booting from the ubuntu live CD and from the terminal SUDO GRUB-INSTALL (hd0).

If I were to try this what would happen - would my existing semi-working grub.config/menu.lst be over ridden with the ubuntu options only or will ubuntu be added? 

Any assistance will be greatly appricated

Thanks

---

### Post by catlett on 2006-08-15
Are saying that the grub menu.lst fron Ubuntu /boot/grub did not work? 
One thing I notice is that you don't have a boot flag for ubuntu's root. The * before the partition signifies that a boot flag is on.
Try this```
 sudo cfdisk /dev/hdg5
``` Toggle the bootable flag on. Then reboot and see what happens.

Wait a minute your in FC5. Su to a root terminal and enter cfdisk /dev/hg5.

---

