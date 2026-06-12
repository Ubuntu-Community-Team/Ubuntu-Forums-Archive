---
title: "[SOLVED] GRUB guru advice needed"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by peithos on 2008-02-13
Hi,

I have Ubuntu 7.10 on first drive on IDE cable and WinXP on second drive - both PATA drives. Both boot perfectly when I set each drive to boot in BIOS.
However when I edit menu.lst to boot WinXP from GRUB I get error 22 and 23 etc. GRUB is on the MBR of the Ubuntu drive. Have tried all the tricks I know but just can't get WinXP to boot. I installed Ubuntu after WinXP and as it installed it recognised WinXP offering to import various settings, and as you can see below it 'automagically' entered a (incorrect) entry for WinXP in menu.lst !!
Below I have posted current menu.lst and device.map details as well as the output from 'sudo fdisk -lu'. Windows appears to be on 'sdb' (300GB), Ubuntu on 'sda' (160GB) and sdc (it's a 200GB SATA drive) is data storage only.
Can anyone suggest the correct edit for the menu.lst file please? Thanks in advance...

Peithos



Details of menu.lst:
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=777ad66c-dc1c-4c29-b7f1-7c194ada2128 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=777ad66c-dc1c-4c29-b7f1-7c194ada2128 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

Details of device.map:
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

Output from sudo fdisk -lu
xxxx@xxxx:~$ sudo fdisk -lu
[sudo] password for xxxx:

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e4481

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    37110149    18555043+  83  Linux
/dev/sda2        37110150    39070079      979965   82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcf26cf26

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   108021059    54010498+   7  HPFS/NTFS
/dev/sdb2       108021060   586099394   239039167+   5  Extended
/dev/sdb5       108021123   292897079    92437978+   7  HPFS/NTFS
/dev/sdb6       292897143   586099394   146601126    7  HPFS/NTFS

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x99d811a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc2   *       16065   398283479   199133707+   5  Extended
/dev/sdc5           16128   398283479   199133676    7  HPFS/NTFS

---

### Post by ajgreeny on 2008-02-13
Not certain, but I think this may be because you have windows on the second disk and it needs to be on the first.  I believe there is a way to get round this with a different mapping arrangement, which I'm sure will be forthcoming from someone else, or you may find it yourself.  Search for "map windows to second drive" or something similar to see if you can shed any light on the problem.

---

### Post by peithos on 2008-02-13
OK sorted.
Needed to edit menu .lst to;
title		Microsoft Windows XP Home Edition
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

Left device.map as was.

I think GRUB/Ubuntu see the drive order different from BIOS. The above menu.lst is 'wrong' but it is correct in that it allows WinXP to dual boot from GRUB on theMBR of the Ubuntu hard-disk. I might think from the output of 'sudo fdisk -lu' that hd2 is the drive sdc with only data, but in menu.lst it points to sdb where WinXP lives!! Strange!!

---

