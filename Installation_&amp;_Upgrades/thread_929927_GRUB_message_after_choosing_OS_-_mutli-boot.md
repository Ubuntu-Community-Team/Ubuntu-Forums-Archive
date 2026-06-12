---
title: "GRUB message after choosing OS - mutli-boot"
date: 2008-09-25
forum: Installation &amp; Upgrades
---

### Post by Sh00nya on 2008-09-25
I have a triple boot desktop with Windows Server 2008 (hd1), Ubuntu Hardy (hd2) & FreeBSD 7 (hd3) on three separate HDDs, with Ubuntu being the default OS and GRUB the boot loader.

I recently upgraded to Windows Server 2008 from 2003, and as I anticipated, Windows overwrote the GRUB entry in MBR of the first disk, which happens to be the disk where Windows is installed.

After upgrading, when I rebooted the system, as expected GRUB menu was gone and only Windows Boot manager showed up with the display options.

I restored GRUB by using Knoppix Live CD. But now, another, if you may call problem or an irritating scenario shows up every time I boot into any of the OSs...and that is that immediately after I select the OS to boot into, and before the boot process of that OS starts, the corresponding entry for the same OS in the menu.lst file gets displayed on the screen...like when I boot into Ubuntu, I see the following message on the screen:

Booting into Ubuntu....
root (hd1,0)
root /vmlinuz
default...

and so on before I see the Ubuntu splash screen and the progress bar showing the boot process.

This kind of message is also displayed when I choose to boot into other OSs. Like if I choose Windows Server, before the Windows boot loader gets displayed, I see the corresponding menu.lst entry for windows, and same with FreeBSD 7.

I was wondering if there is a way of stopping these messages from being displayed. I would really appreciate any insight forum members might be able to offer into resolving this issue. Thanks in advance!

---

### Post by caljohnsmith on 2008-09-25
Please post your menu.lst:
```
cat /boot/grub/menu.lst
```
That might be where the problem is, but what version of Grub does that Knoppix Live CD use? And how did you restore grub with it, by using "root" and "setup" in the Grub CLI, or did you use the "grub-install" command?

---

### Post by Sh00nya on 2008-09-25
Thanks caljohnsmith for responding to my post. I appreciate!

Now wrt your queries, I used Knoppix 5.1 Live CD, and GRUB version is 0.97, which shows up on top of the GRUB menu. I restored GRUB by trial & error method meaning using both "grub-install" as well as "root" & "setup" command in the GRUB shell. This was due to the reason that a couple of times while trying to restore GRUB, using "setup" command, I didn't realise that I was entering wrong hard drive (hd1) as argument for it, instead of the correct hd0, where MBR is. I was able to later correct this mistake and thereby restrore GRUB.

BTW, here's my menu.lst file:

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
# kopt=root=UUID=b026706d-e0ec-4f7d-9c76-bde9b5be413b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-386 root=UUID=b026706d-e0ec-4f7d-9c76-bde9b5be413b ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-386
quiet
savedefault

title		Ubuntu 8.04.1, kernel 2.6.24-19-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-386 root=UUID=b026706d-e0ec-4f7d-9c76-bde9b5be413b ro single
initrd		/boot/initrd.img-2.6.24-19-386

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b026706d-e0ec-4f7d-9c76-bde9b5be413b ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b026706d-e0ec-4f7d-9c76-bde9b5be413b ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-386 root=UUID=b026706d-e0ec-4f7d-9c76-bde9b5be413b ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-386
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-386 root=UUID=b026706d-e0ec-4f7d-9c76-bde9b5be413b ro single
initrd		/boot/initrd.img-2.6.24-18-386

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=b026706d-e0ec-4f7d-9c76-bde9b5be413b ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=b026706d-e0ec-4f7d-9c76-bde9b5be413b ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title		FreeBSD 7.0
root		(hd2,0,a)
kernel		/boot/loader
savedefault
makeactive
chainloader	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by caljohnsmith on 2008-09-25
Are you sure you can successfully boot into FreeBSD? Your Grub menu entry for it is:
```
title FreeBSD 7.0
root [COLOR="Red"](hd2,0,a)[/COLOR]
kernel /boot/loader
savedefault
makeactive
chainloader +1
```
The highlighted syntax shouldn't work with Grub. Please post the output of the following commands while in Ubuntu:
```

sudo fdisk -lu
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump
sudo dd if=/dev/sdc bs=1 skip=1049 count=2 2>/dev/null | hexdump
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
grub> quit
```
Also, do you know for sure which HDD you boot from on start up?

---

### Post by meierfra. on 2008-09-25
caljohnsmith:  From the  grub manual:

 >     (hd1,a)
      This means the BSD ‘a’ partition of the second hard disk. If you need to specify which pc slice number should be used, use something like this: ‘(hd1,0,a)’. If the pc slice number is omitted, GRUB searches for the &#64257;rst pc slice which has a BSD ‘a’ partition.

---

### Post by Sh00nya on 2008-09-25
Yes, I can successfully boot into FreeBSD. BTW, its the first HDD (hd0), where Windows Server is installed, I boot from on startup.

Here's the output of the commands you listed:

sudo fdisk -lu

Disk /dev/sda: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders, total 40132503 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd7a3d7a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     3534299     1767118+   6  FAT16
/dev/sda2         3534300    40130369    18298035    f  W95 Ext'd (LBA)
/dev/sda5         3534363     3630689       48163+   7  HPFS/NTFS
/dev/sda6         3630753    40130369    18249808+   7  HPFS/NTFS

Disk /dev/sdb: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders, total 40132503 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2793359e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    13671314     6835626   83  Linux
/dev/sdb2        13671315    17575109     1951897+  82  Linux swap / Solaris
/dev/sdb3        17575110    23711939     3068415   83  Linux
/dev/sdb4        23711940    40130369     8209215    5  Extended
/dev/sdb5        23712003    40130369     8209183+  83  Linux

Disk /dev/sdc: 20.5 GB, 20547841536 bytes
16 heads, 63 sectors/track, 39813 cylinders, total 40132503 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd02fd02f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    40131503    20065720+  a5  FreeBSD

*******
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
0000000 8100                                   
0000002

sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump
0000000 ff00                                   
0000002

sudo dd if=/dev/sdc bs=1 skip=1049 count=2 2>/dev/null | hexdump
0000000 0000                                   
0000002

*******

grub> find /boot/grub/stage1
(hd1,0)

grub> find /grub/stage1
Error 15: File not found

---

### Post by caljohnsmith on 2008-09-25
> **meierfra. said:**
> caljohnsmith:  From the  grub manual:
> (hd1,a)
This means the BSD ‘a’ partition of the second hard disk. If you need to specify which pc slice number should be used, use something like this: ‘(hd1,0,a)’. If the pc slice number is omitted, GRUB searches for the &#64257;rst pc slice which has a BSD ‘a’ partition. 
My ignorance, thanks for pointing that out, meierfra. Guess it shows how much I've had to deal with BSD with Grub. :)

---

### Post by caljohnsmith on 2008-09-26
Sh00nya, did you ever use "gfxboot" in Ubuntu at some point to get a fancy Grub splash screen? I'm just wondering because I think that gfxboot might have that type of behavior you describe, where the Grub boot stanzas are all echoed to your screen right after you boot an OS. But I don't see any reference in your menu.lst to gfxboot, so I could be completely wrong.

---

### Post by Sh00nya on 2008-09-26
> **caljohnsmith said:**
> Sh00nya, did you ever use "gfxboot" in Ubuntu at some point to get a fancy Grub splash screen? I'm just wondering because I think that gfxboot might have that type of behavior you describe, where the Grub boot stanzas are all echoed to your screen right after you boot an OS. But I don't see any reference in your menu.lst to gfxboot, so I could be completely wrong.
No caljohnsmith! I never used "gfxboot" or any other software apart from Knoppix Live CD.

---

