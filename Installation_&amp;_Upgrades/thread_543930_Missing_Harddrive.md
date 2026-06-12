---
title: "Missing Harddrive"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by doddi on 2007-09-05
Hi People,

I have previously installed Ubuntu Feisty 7.04 on another machine dual booting between XP, so I am fairly familiar with the requirements for dual booting. I have also managed (just about) to do the same on  second machine running vista, after many hours trying to get the damn thing to re-partition.
So I decided to give this a go on my new PC that came with Vista. However my main problem I am having is when using the liveCD, ubuntu doesnt recognise my drive or any of the partitions within the drive, they are not mounted and gparted cant see them.

My machine is an Intel Core2 320GB SATA hard drive partitioned (RAID disabled) as 160GB (vista), 60GB(not allocated), 100GB (ntfs data)

Any help really appreciated!

doddi

---

### Post by Pumalite on 2007-09-05
Partition with Vista's partitioner, then use Gparted to format new partition to ext3, then Install.

---

### Post by merlinus on 2007-09-05
The ubuntu installer will not recognize unallocated space.  Use gparted live cd to format it, and then you will be able to install ubuntu into that 60G partition.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by doddi on 2007-09-05
I will try that but it doesnt see ANY of my drive including the already existing ntfs partitions of vista and data.

Thx anyway if that does work :)

doddi

---

### Post by Pumalite on 2007-09-05
If you have no luck with Gparted, use rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
It has a partitioner that succeeds where Gparted fails.

---

### Post by doddi on 2007-09-05
Thx for the info guys but it didnt help.

I dont think the problem is anything to do with the partitions because like i said it cant see the Vista partition or data partition. I also checked Hardware information and I dont see the drive in the list at all! :confused:

I havent tried the suggestion of rescuecd -  i will try tomorrow thx

doddi

---

### Post by doddi on 2007-09-06
OK, now I am really confused.

The only way I managed to get Ubuntu to see my physical drive was to change the BIOS so that it was classed as a RAID drive. All intalls and runs fine! BUT I am now left unable to boot Vista without changing the BIOS back to IDE.

Does anyone have any idea what is going on! I am so confused.

Thanks in advance

doddi

---

### Post by Pumalite on 2007-09-06
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by doddi on 2007-09-07
Thanks for trying to help Pumalite, this is obviously when I have my drive set to RAID otherwise ubuntu doesnt recognise the drive as present at all.

Here are the outputs you asked for:

Fdisk:
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   163846934    81922443+   7  HPFS/NTFS
/dev/sda2       342595584   563699711   110552064    7  HPFS/NTFS
/dev/sda3       163846935   342586124    89369595    5  Extended
/dev/sda4       563704785   625137344    30716280    b  W95 FAT32
/dev/sda5       163846998   167943509     2048256   82  Linux swap / Solaris
/dev/sda6       167943573   342586124    87321276   83  Linux

Partition table entries are not in disk order

```

Grub:
```

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=9906efeb-1ca8-4617-93dc-268b51c49c8d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=9906efeb-1ca8-4617-93dc-268b51c49c8d ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=9906efeb-1ca8-4617-93dc-268b51c49c8d ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by Pumalite on 2007-09-07
Your original post stated you were using the Live CD, but what I see here; besides Windows in sda1, is a Linux system installed in sda6 and a Grub that is pointing in the right direction in both cases (Windows and Ubuntu). So if you cannot boot we'll have to examine the issue of your Raid. What is the problem at the present time (because this tread has gone on a long time)?.

---

### Post by doddi on 2007-09-07
Sorry, maybe i didnt explain myself fully.

Turn on my computer that is pre-installed with Vista. For Vista to run the BIOS is set to IDE. In this state whenever I boot up the liveCD my SATA drive would not be detected.

After a lot of fiddling about and pulling my hair out  I changed the BIOS setting to RAID, and to my surprise the live CD detected my SATA drive (although on startup the BIOS complains that it cant find any RAID drive before the liveCD kicks in). With it still in the RAID setting I was able to do a complete install and run ubuntu fine even after reboots

The problem I have is that now I have the situation were I am required to change my BIOS setting to run either Ubuntu or Vista.
Ubuntu -> BIOS requires RAID setting ...my drive is not a RAID drive!
Vista -> BIOS requires original setting of IDE.

Thanks again

---

### Post by Pumalite on 2007-09-07
This then maybe a BIOS problem. Try updating your BIOS

---

### Post by doddi on 2007-09-07
Ok thx Pumalite, I will give that a go

doddi

---

