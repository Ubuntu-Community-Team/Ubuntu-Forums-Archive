---
title: "Dual boot error: GRUB error 21"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by invise on 2008-04-24
I've included relevant computer specs at the bottom of this post, but I'll explain the problem I've encountered, while installing 8.04LTS, in detail here.

I want to dual boot Windows XP and Linux (a common problem).  My BIOS is configured for RAID; Windows is installed on two 320GB sata drives (sda and sdb) in RAID 0, and that array is set as the primary boot device.  The secondary boot device is a 750GB sata drive (sdc) with two partitions sdc1 (640GB) and sdc2 (110GB).  Ubuntu 8.04LTS x86 desktop is installed on sdc2, formatted in ext3.

The problem: after restarting after the install, the system will not boot to either Windows or Ubuntu.  The error given is GRUB loading, error 21.  Switching the primary boot device to the 750GB drive with Ubuntu on one partition does not solve the problem - instead, the BIOS prompts to insert a boot disk.

The question: is it possible to dual boot when the two OS are on different disks?  When one is a RAID array and the other is not?  How do I need to alter files in Windows and/or Ubuntu in order to set up dual booting?

```
System specs:

version
Ubuntu 8.04LTS, desktop x86

hardware
sda: 320GB sata
sdb: 320GB sata
sdc: 750GB sata

partitions
640GB ntfs on 2x 320GB (raid 0)
640GB ntfs on 750GB
110GB ext3 on 750GB
```

From reading a couple of other topics around here, I've tried to include some other relevant information as well.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf026f026

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       77825   625129281    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x320a1743

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23f235bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       77825   625129281    7  HPFS/NTFS
/dev/sdc2           77826       91201   107442720   83  Linux
```

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# kopt=root=UUID=f05f8101-e166-4b37-92e7-fc8b0efc291c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,1)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f05f8101-e166-4b37-92e7-fc8b0efc291c ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f05f8101-e166-4b37-92e7-fc8b0efc291c ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd2,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by invise on 2008-04-24
It's also worth noting that physically disconnecting the drive Ubuntu is installed on yields no change.  Somehow, in the process of installing Ubuntu, something in the Windows installation or in the boot process was changed and is causing the boot problem.

What kind of file would the Ubuntu installation process have altered?  How can/do I edit it?


<edit> I suspect that maybe Ubuntu tried to write a boot file or record of some sort to my Windows installation to tell it to acknowledge Ubuntu as a booting option, but only wrote it to one drive of the array.  It looks like Ubuntu doesn't recognize the RAID array.  Selecting "boot from first drive" on the initial Live CD menu yields the same GRUB error 21 message.  Maybe all of this can be solved by getting the Live CD to recognize the RAID array and therefore let me edit Windows files?

---

### Post by confused57 on 2008-04-25
You can use the Ubuntu live cd to install grub's IPL(Initial Program Loader) to the Ubuntu drive's mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
It would be something like:
```
root (hd2,1)
setup (hd2)
```

You "should" get a grub boot menu when you boot first to the Ubuntu drive, but you'll need to edit the root line by highlighting the first Ubuntu entry, press "e", highlight the line with root, press "e" again, change root from (hd2,1) to (hd0,1), press "enter", then "b" to boot.  This change is temporary, but you can make it permanent:
```
gksudo gedit /boot/grub/menu.lst
```

If you're able to get your system to boot, you might consider reinstalling Window's IPL to the mbr of your first Window's drive:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
This way if for some reason Ubuntu doesn't boot, you can change your bios to boot first to the Window's drive(s).

---

### Post by invise on 2008-04-25
Thank you, your suggestions to fix Ubuntu's MBR worked and I'm able to boot to Ubuntu on the single disk.  That's worth something.

However, the second step - fixing Windows' MBR via recovery console - will not work.  Ubuntu still doesn't recognize my RAID array, because it's [fakeRAID](https://help.ubuntu.com/community/FakeRaidHowto); if I want the Windows CD to see RAID disks (by slipstreaming drivers), I lose access to the Recovery Console (thanks Microsoft).  Unless I can get Ubuntu to recognize my array so that I can find and edit some Windows boot file on it, I'm going to have to format it.

---

### Post by confused57 on 2008-04-25
> **invise said:**
> Thank you, your suggestions to fix Ubuntu's MBR worked and I'm able to boot to Ubuntu on the single disk.  That's worth something.

However, the second step - fixing Windows' MBR via recovery console - will not work.  Ubuntu still doesn't recognize my RAID array, because it's [fakeRAID](https://help.ubuntu.com/community/FakeRaidHowto); if I want the Windows CD to see RAID disks (by slipstreaming drivers), I lose access to the Recovery Console (thanks Microsoft).  Unless I can get Ubuntu to recognize my array so that I can find and edit some Windows boot file on it, I'm going to have to format it.
Try downloading a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Set your 1st Windows drive as the primary boot device in bios, boot SGD, then look for an option to "Fix Boot of Windows".  I believe all you need is to install Windows IPL to the 1st drive's mbr.

---

### Post by invise on 2008-04-25
Once again, your suggestion was right on.  SuperGRUB on CD was able to remove GRUB from hd0 and, sure enough, Windows can boot.  Ubuntu's MBR is still intact, so I can also boot Ubuntu if hd2 is set to first boot device.  It isn't a dual-boot system yet, and Ubuntu doesn't still doesn't recognize RAID, but I think I can figure those out from here.

Thanks again for your help; this topic can be closed now.

---

### Post by confused57 on 2008-04-25
> **invise said:**
> Once again, your suggestion was right on.  SuperGRUB on CD was able to remove GRUB from hd0 and, sure enough, Windows can boot.  Ubuntu's MBR is still intact, so I can also boot Ubuntu if hd2 is set to first boot device.  It isn't a dual-boot system yet, and Ubuntu doesn't still doesn't recognize RAID, but I think I can figure those out from here.

Thanks again for your help; this topic can be closed now.
You should be able to boot Windows from grub, you would need to change the root from (hd0,x) to (hd1,x) and add mapping lines, e.g.
```
title  Windows
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

To edit your menu.lst, open a terminal:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
Add the above Windows at the very end of your menu.lst(after the line ###END DEBIAN AUTOMAGIC KERNELS LIST)...quit & save.

Added:  I assume you changed all your Ubuntu root lines to (hd0,1)...you also need to change the line with #groot to (hd0,1):
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)
leave the # in front of groot.

---

