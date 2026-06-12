---
title: "Problem with dual boot"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by canatolie on 2008-11-03
Hi there,

My situation is like: I have a PC with 2 hdds (80GB-with 3 NTFS partitions where is installed windows xp on C: and a 20,5GB - 2 partitions: first is ext3 with Ubuntu 8.10 on it and a FAT32).

What I did was: Removed 80Gb hdd and installed Ubuntu 8.10 over my older 7.10 version but before that I've formated ext3 partition. After that, I've installed back the 80Gb hdd and booting ok into my fresh 8.10. There is no problem seeing my ntfs partitions. 

The thing is that I can't boot into my Windows XP. I've modified the /boot/grub/menu.lst and on the GRUB Boot Screen appears the winxp selection. But everytime I choose it, it gives me an error (last one: "Error 23: Error while parsing number...").

This is my problem. Please help!

Thanks in advance,

Anatolie

---

### Post by caljohnsmith on 2008-11-03
Please first post:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```
And we can work from there. :)

---

### Post by canatolie on 2008-11-03
root@CAM:~# fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41fd41fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    41206724    20603331    7  HPFS/NTFS
/dev/sda2        41206725   156280319    57536797+   f  W95 Ext'd (LBA)
/dev/sda5        41206788    82558034    20675623+   7  HPFS/NTFS
/dev/sda6        82558098   156280319    36861111    7  HPFS/NTFS

Disk /dev/sdb: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders, total 40132503 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xabf4abf4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63      546209      273073+  83  Linux
/dev/sdb2          546210    40130369    19792080    f  W95 Ext'd (LBA)
/dev/sdb5        15631308    40130369    12249531    b  W95 FAT32
/dev/sdb6          546336    14876189     7164927   83  Linux
/dev/sdb7        14876253    15631244      377496   82  Linux swap / Solaris

Partition table entries are not in disk order
root@CAM:~# cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		15

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e8604c87-5f0f-49be-832d-c8eee0e8f5ff ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e8604c87-5f0f-49be-832d-c8eee0e8f5ff

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Microsoft Windows XP Professional
root (sd0,0)
savedefault
makeactive 
chainloader +1

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		e8604c87-5f0f-49be-832d-c8eee0e8f5ff
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e8604c87-5f0f-49be-832d-c8eee0e8f5ff ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		e8604c87-5f0f-49be-832d-c8eee0e8f5ff
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e8604c87-5f0f-49be-832d-c8eee0e8f5ff ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		e8604c87-5f0f-49be-832d-c8eee0e8f5ff
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
root@CAM:~#

---

### Post by caljohnsmith on 2008-11-03
OK, first open your menu.lst
```
gksudo gedit /boot/grub/menu.lst
```
First delete your existing Windows entry, and at the end very end of the file, add the following Windows entry:
```
title Microsoft Windows XP Professional
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

```
Reboot, and let me know if that works. If it doesn't, let me know exactly what happens when you select it from the Grub menu.

---

### Post by canatolie on 2008-11-03
Dear caljohnsmith,

Really thanks!!!!  You are super great! I'm already in my Windows XP. Everything works just fine. Google is nothing :D If to compare to your knowledge!

Many thanks & Best regards,

Anatolie

---

### Post by caljohnsmith on 2008-11-03
That's great you can boot into Windows now, and I'm glad your booting problem was so easy to solve; cheers and have fun. :)

---

