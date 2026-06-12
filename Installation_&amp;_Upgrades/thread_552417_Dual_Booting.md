---
title: "Dual Booting"
date: 2007-09-16
forum: Installation &amp; Upgrades
---

### Post by rick83 on 2007-09-16
Hi,

I am having probs dual booting on my laptop. I have installed WinXP prior to ubuntu.
I have googled lots and not much luck, When i select my windows boot it says:

"Error 21 : Disk not found" or someth of that sort.

my fdisk

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2335df7d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       15553   104446597+   f  W95 Ext'd (LBA)
/dev/sda3           15554       15675      979965   82  Linux swap / Solaris
/dev/sda4           15676       19457    30378915   83  Linux
/dev/sda5            2551       15553   104446566    b  W95 FAT32


my menu.1st

rick@ubuntu:~$ sudo cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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

#title Microsoft Windows XP 
#root (hd0,1)
#savedefault
#makeactive
#chainloader +1

title Windows
rootnoverify (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader (0,1)+1

title winxp
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd0,0)
makeactive 
chainloader (hd1,0)+1

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
# kopt=root=UUID=6bf2dd9f-9f05-4ee1-b717-20c9b6a06a2e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

title           Ubuntu gutsy (development branch), kernel 2.6.22-11-generic
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.22-11-generic root=UUID=6bf2dd9f-9f05-4ee1-b717-20c9b6a06a2e ro quiet splash
initrd          /boot/initrd.img-2.6.22-11-generic
quiet

title           Ubuntu gutsy (development branch), kernel 2.6.22-11-generic (recovery mode)
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.22-11-generic root=UUID=6bf2dd9f-9f05-4ee1-b717-20c9b6a06a2e ro single
initrd          /boot/initrd.img-2.6.22-11-generic

title           Ubuntu gutsy (development branch), memtest86+
root            (hd0,3)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Pumalite on 2007-09-16
[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

If you happen to be using a hard disk larger than 137 GB, see also error 18.

[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

---

### Post by rick83 on 2007-09-16
hi,

sorry i forgot to mention that its one physical disk.

---

### Post by Pumalite on 2007-09-16
That's OK. I saw it in your fdisk, that's why I made the note about disks larger than 137 GB and the link for you to peruse.

---

### Post by rick83 on 2007-09-16
i have flashed my bios. and my laptop is using a SATA hd

---

### Post by Pumalite on 2007-09-16
And your hard disk detection is on 'Auto'?.

---

### Post by logos34 on 2007-09-16
try this:

> title Windows XP
root (hd0,0)
makeactive
chainloader +1

---

### Post by Pumalite on 2007-09-16
Logos34 is the MAN, so I leave you in good hands.

---

### Post by logos34 on 2007-09-16
> **Pumalite said:**
> Logos34 is the MAN

Is something bothering you, Pumalite?

---

### Post by Pumalite on 2007-09-16
Are you kidding me?. I respect you and think that you are more knowledgeable than me. That's all.

---

### Post by logos34 on 2007-09-16
Alright.  I just thought for a second I detected some sarcasm.  nm.  You'd be surprised at what I don't know--that's why I hang out in these forums.  Troubleshooting other people's problems helps me learn about linux...or rather helps me learn how much I still don't know about linux! ;-)

---

### Post by Pumalite on 2007-09-16
I'm glad logos. I feel the same. I also learn from this forum. May the Ubuntu be with you!

---

### Post by RavanH on 2007-09-16
Hi,

Maybe I should create a new thread but let me just ask here first:

I have had a dual-boot setup (WinXP + Feisty) running fine but decided to try out the new Gutsy testing (tribe5) and decided to do a clean install on a new partition. But after installation there are no references to the new Gutsy in grub so I cannot boot into the new install.

How can I make my system triple-boot Feisty + Gutsy + WinXP. Should I manually edit menu.lst or are there any grub calls that will add the new install automatically?

Thanks :)

---

### Post by Pumalite on 2007-09-16
I you installed Tribe 5 well, you would now be looking at Tribe 5's Grub. Post:
sudo fdisk -lu
cat /boot/grub/menu,lst

---

### Post by RavanH on 2007-09-16
> **Pumalite said:**
> I you installed Tribe 5 well, you would now be looking at Tribe 5's Grub.
I did install tribe5 (but only from safe graphics mode, else boot from cd didn't work) but after the installation process i rebooted and got to see my old grub menu with no entry for the new installation...
```
~$ sudo fdisk -lu
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2df62df5

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63     8401994     4200966   1b  Hidden W95 FAT32
/dev/hda2   *     8401995    37061954    14329980    7  HPFS/NTFS
/dev/hda3        37061955    65721914    14329980   83  Linux
/dev/hda4        65721915   156296384    45287235    f  W95 Ext'd (LBA)
/dev/hda5        65721978   107667629    20972826    b  W95 FAT32
/dev/hda6       149613471   152954864     1670697    7  HPFS/NTFS
/dev/hda7       152954928   156296384     1670728+  82  Linux swap / Solaris
/dev/hda8       107667693   128648519    10490413+  83  Linux
/dev/hda9       128648583   149613344    10482381   83  Linux

Partition table entries are not in disk order
```

and

```
~$ cat /boot/grub/menu.lst
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# kopt=root=UUID=560d2c76-57b4-4cfb-ad80-582e1201e0e9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# defoptions=quiet splash rootflags=data=writeback locale=nl_NL

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
# altoptions=(recovery mode) single rootflags=data=writeback

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

title		Ubuntu, kernel 2.6.22-11-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-11-generic root=UUID=560d2c76-57b4-4cfb-ad80-582e1201e0e9 ro quiet splash rootflags=data=writeback locale=nl_NL
initrd		/boot/initrd.img-2.6.22-11-generic
quiet

title		Ubuntu, kernel 2.6.22-11-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-11-generic root=UUID=560d2c76-57b4-4cfb-ad80-582e1201e0e9 ro single rootflags=data=writeback
initrd		/boot/initrd.img-2.6.22-11-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Packard Bell - Factory Restore Setup (Windows XP)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

Oh, and thanks for your quick reply :)

---

### Post by Pumalite on 2007-09-16
Try re-installing Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by RavanH on 2007-09-17
ok, will give it a try... thanks for your help :)

---

