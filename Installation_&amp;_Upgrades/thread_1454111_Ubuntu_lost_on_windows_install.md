---
title: "Ubuntu lost on windows install"
date: 2010-04-14
forum: Installation &amp; Upgrades
---

### Post by abicash on 2010-04-14
Hello

I have lost ubuntu (or "grub" to be precise) after windows install.Please help me revive ubuntu!

Some things you may be interested in
```
 sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x27822781

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    43471889    21735913+   c  W95 FAT32 (LBA)
/dev/sda2        43471890   312576704   134552407+   f  W95 Ext'd (LBA)
/dev/sda5        43471953    57352049     6940048+   b  W95 FAT32
/dev/sda6        57352113   118784609    30716248+   7  HPFS/NTFS
/dev/sda7       118784673   180217169    30716248+   7  HPFS/NTFS
/dev/sda8       180217233   241649729    30716248+   7  HPFS/NTFS
/dev/sda9       241649793   312576704    35463456    7  HPFS/NTFS

Disk /dev/sdb: 20.0 GB, 20060135424 bytes
255 heads, 63 sectors/track, 2438 cylinders, total 39179952 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1cc1b2a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63     3903794     1951866   82  Linux swap / Solaris
/dev/sdb2   *     3903795    24868619    10482412+  83  Linux
/dev/sdb3        24868620    39166469     7148925    b  W95 FAT32

```



And in grub
 ```
grub> root (hd1,2)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

```

My menu.lst
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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		2

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

#A splash image for the menu
splashimage=/boot/grub/splashimages/Mac4Lin_GRUB1_v1.0.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=6cb21820-1cb7-45db-bac6-3a13e951bf1f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6cb21820-1cb7-45db-bac6-3a13e951bf1f

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

title		Ubuntu 8.10 Intrepid
root 		hd(1,2)
uuid		6cb21820-1cb7-45db-bac6-3a13e951bf1f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6cb21820-1cb7-45db-bac6-3a13e951bf1f ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, (recovery mode)
root 		hd(1,2)
uuid		6cb21820-1cb7-45db-bac6-3a13e951bf1f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6cb21820-1cb7-45db-bac6-3a13e951bf1f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

#title		Ubuntu 8.10, memtest86+
#uuid		6cb21820-1cb7-45db-bac6-3a13e951bf1f
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Expecting help from forum members :)

---

### Post by Mighty_Joe on 2010-04-14
A quick search on Google returns many HOWTO's, including the [Ubuntu Community Documentation]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") and [Howto Geek]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/")

---

### Post by oldfred on 2010-04-14
In old grub partitions start at 0 (changed in grub2).

Your root (1,2) is the third partition.

for sda2  where you install is, it is root (1,1)

---

### Post by abicash on 2010-04-16
> **Mighty_Joe said:**
> A quick search on Google returns many HOWTO's, including the [Ubuntu Community Documentation]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") and [Howto Geek]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/")

None have worked for me so far... :(

[QUOTE=oldfred] In old grub partitions start at 0 (changed in grub2).

Your root (1,2) is the third partition.

for sda2 where you install is, it is root (1,1) 

[/QUOTE]

i have 2 hard disks and linux is on sdb2

Please can you help??

---

### Post by coffeecat on 2010-04-16
> **abicash said:**
> i have 2 hard disks and linux is on sdb2

From the fdisk output of your first post, that seems correct. However....

> **abicash said:**
> 
 ```
grub> root (hd1,2)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

```My menu.lst
```
<snip>
title        Ubuntu 8.10 Intrepid
root         hd(1,2)
uuid        6cb21820-1cb7-45db-bac6-3a13e951bf1f
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=6cb21820-1cb7-45db-bac6-3a13e951bf1f ro quiet splash vga=791
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

<snip>
```

You are using legacy grub and sdb2 in legacy grub speak is (hd1,1), not (hd1,2). In legacy grub, partitions are numbered from 0. In grub2, partitions are numbered from 1. Perhaps that's where the confusion arose.

So, those grub commands (I presume from a live disc?) need to be:

```
root (hd1,1)
setup (hd0)
```'setup' needs to point to sda/(hd0) to install grub stage 1 to the mbr of your primary hard drive.

But there's also a problem with your menu.lst. That stanza is referring to "hd(1,2)". Note the erroneous position of the brackets and the numbering of the partition. It also needs to be (hd1,1). Also, you've got both a 'root' line and an 'uuid' line. You don't need both. I don't know, but that might confuse grub once you've reinstalled it to the mbr.

Last comment: you are running Intrepid. That will reach end of life in a few days. You may wish to think about upgrading.

---

### Post by abicash on 2010-04-16
Got it working thanks....:P

---

### Post by coffeecat on 2010-04-16
Excellent! :)

---

