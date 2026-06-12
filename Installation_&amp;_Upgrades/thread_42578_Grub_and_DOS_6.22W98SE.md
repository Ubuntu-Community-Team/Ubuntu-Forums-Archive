---
title: "Grub and DOS 6.22/W98SE"
date: 2005-06-18
forum: Installation &amp; Upgrades
---

### Post by LinuxFan9 on 2005-06-18
Hi there,

I have two harddisks in my computer.
The first of them containing: DOS 6.22, Win98SE und another different Win98SE.
All of them were installed on their own partition (C:). Two of  these partitions were always invisible, the third visible and active for booting the system. Using another system I had to switch the staus from invisiblle to visible - for example DOS 6.22 - and from visible to invisible - for example Win98SE. So  Icould use  all of the three OS.
Then I installed Ubuntu in an own partition.
Grub did recognize all - three - Operating Systems and was installed in the MBR of the first harddisk. 
Booting with Grub - with selection menu from Grub: Linux, DOS, Win98, Win98 - results in:
- Linux ok.
- DOS - showing: starting MS-DOS on screen - and nothing else
- Win98SE - only one/the same Version of Win98Se is always started 
Why this?

Thadeus

*****************
fdisk -l shows:
Platte /dev/hda: 81.9 GByte, 81964302336 Byte
255 Köpfe, 63 Sektoren/Spuren, 9964 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes

Gerät boot. Anfang Ende Blöcke Id System
/dev/hda1 1221 2941 13823932+ f W95 Erw. (LBA)
/dev/hda2 777 1220 3566430 c W95 FAT32 (LBA)
/dev/hda3 * 1 261 2096451 16 Verst. FAT16
/dev/hda4 320 776 3670821 1b Verst. W95 FAT32
/dev/hda5 1221 1475 2048256 b W95 FAT32
/dev/hda6 1476 2176 5630751 b W95 FAT32
/dev/hda7 2177 2941 6144831 83 Linux

Partitionstabelleneinträge sind nicht in Platten-Reihenfolge

Platte /dev/hdb: 30.7 GByte, 30738677760 Byte
16 Köpfe, 63 Sektoren/Spuren, 59560 Zylinder
Einheiten = Zylinder von 1008 × 512 = 516096 Bytes

Gerät boot. Anfang Ende Blöcke Id System
/dev/hdb1 * 54482 59560 2559816 f W95 Erw. (LBA)
/dev/hdb5 54482 56513 1024096+ b W95 FAT32
/dev/hdb6 56514 58544 1023592+ b W95 FAT32
/dev/hdb7 58545 59560 512032+ 82 Linux Swap / Solaris

**********************
menu.lst (Grub) shows:

default 0
timeout 10

title Ubuntu, kernel 2.6.10-5-686
root (hd0,6)
kernel /boot/vmlinuz-2.6.10-5-686 root=/dev/hda7 ro quiet splash
initrd /boot/initrd.img-2.6.10-5-686
savedefault
boot

title Ubuntu, kernel 2.6.10-5-686 (recovery mode)
root (hd0,6)
kernel /boot/vmlinuz-2.6.10-5-686 root=/dev/hda7 ro single
initrd /boot/initrd.img-2.6.10-5-686
savedefault
boot

title Ubuntu, kernel 2.6.10-5-386
root (hd0,6)
kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/hda7 ro quiet splash
initrd /boot/initrd.img-2.6.10-5-386
savedefault
boot

title Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root (hd0,6)
kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/hda7 ro single
initrd /boot/initrd.img-2.6.10-5-386
savedefault
boot

title Ubuntu, kernel memtest86+
root (hd0,6)
kernel /boot/memtest86+.bin
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda4
title Windows 95/98/Me
root (hd0,3)
savedefault
makeactive
chainloader +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda3
title MS-DOS 5.x/6.x/Win3.1
root (hd0,2)
savedefault
makeactive
chainloader +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title Windows 95/98/Me
root (hd0,1)
savedefault
makeactive
chainloader +1

---

