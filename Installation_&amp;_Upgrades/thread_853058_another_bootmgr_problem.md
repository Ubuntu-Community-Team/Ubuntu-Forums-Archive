---
title: "another bootmgr problem"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by KhaaL on 2008-07-08
okay, here's my situation... I bought a computer with vista preinstalled, and then quickly installed ubuntu on another harddrive. Since I need a windows enviorment every now and then, I decided to install XP on yet another harddrive. However, since my computer is loaded with a bunch of components I'm not familiar with nor have any drivers for, I decided to stick with vista after all.

The problem is that the installation of XP must have messed up something, since I get the error message that bootmgr is missing. since this is a OEM system, I don't have a installation DVD to do a recovery from. this is weird, since there is a file called bootmgr on my vista partition (428.6 KB).

Is there any way I can repair this from ubuntu?

my fdisk -l:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       40497   306157288+   7  HPFS/NTFS
/dev/sda2           40498       41345     6410880    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x015bc091

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       41345   312568168+  83  Linux

Disk /dev/sdc: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdda1dda1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2962        8772    46676857+  83  Linux
/dev/sdc2               1        2961    23784201   83  Linux
/dev/sdc3            8773        9039     2144677+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdh: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       14593   117218241   83  Linux

```


and grub/menu.list:

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
# kopt=root=UUID=c9776032-3308-4360-b92c-fc8c467d0fa9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c9776032-3308-4360-b92c-fc8c467d0fa9 ro splash rootflags=data=writeback
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c9776032-3308-4360-b92c-fc8c467d0fa9 ro splash rootflags=data=writeback
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c9776032-3308-4360-b92c-fc8c467d0fa9 ro single rootflags=data=writeback
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Restore partition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

thanks in advance for any help :)

---

### Post by charonred on 2008-07-08
Seems to be a few boot manager probs with GRUB; probably GRUB has intalled the bootloader for your Ubuntu install on the disk with Vista installed, instead of the disk Ubuntu is on, and has overwritten the Windows bootloader.

Try booting the computer and and hit F4 (I think) when loading GRUB boot loader to display other boot options including Windows Vista -  may be able to boot to Vista that way.

I've found the safest way to install Ubuntu with GRUB was to physically unplug all other drives not having ubuntu installed, then do the install, that way GRUB bootloader gets installed on that drive instead of the drive XP/Vista is on.

Anyhow, to maybe get Vista loading, you may need to fix GRUBS bootloader - came across this utility [Ikki Boot]("http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Ikki-Boot-33909.shtml")
just burn  .iso to CD, then boot PC on disc and try using Super GRUB which is a repair tool for GRUB bootloader.

I'm going to see if it can fix mine, so can't vouch for it yet, but was recommended on [Distrowatch]("http://distrowatch.com/weekly.php?issue=20080707#news") as a handy tool.

---

### Post by Pumalite on 2008-07-08
Super Grub is a great idea to boot your Vista and to fix it's MBR. You can get it alone too:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by charonred on 2008-07-08
Another option if the above don't work, and as you don't have a Vista disc is to try the following free utility which should get Vista booting again.
[http://www.vistabootpro.org/](http://www.vistabootpro.org/)

---

### Post by KhaaL on 2008-07-09
well guys, i did get super grubdisk and i did run it. But it didn't solve my problem since I got a complaint about a missing \system32\hal.dll file. fortunatly, the recovery partition had a "fix boot" option. However, I can't boot directly into vista, but I have to do boot through the restore partition every time.

I don't how to fully fix my partitions... I don't mind how tings are right now but I'm afraid to screw things up if grub gets reinstalled or something :P

---

### Post by charonred on 2008-07-09
I gave that SuperGrub a  try as well for my Ubuntu install, but didn't help:confused:

So I unplugged all other drives and reinstalled it; before I do anything else with it I'm going to make an image of the drive with functional Ubuntu so any future stuff ups can be fixed quickly, and I suspect I'll have a few over time :lol:

I've been able to fix my own boot in XP using the XP install disc and Restore Console, but Vista is different arrangement. So might be worth giving that VistaBootPro a try, though I understand your reluctance to mess with your OS 'lest it break' altogether.

I've got a broken Vista boot on another drive in my previous PC, so I might have a shot at that and post back later.

---

### Post by KhaaL on 2008-07-09
Yes please, do post about your experience with vistabootpro!

It's too bad that vista has broken compatibility regarding multi-boots...

---

### Post by charonred on 2008-07-10
Hmmmm, well I installed and ran VistaBootPro, and seemed like it fixed the Vista boot, but I still can't boot on that disk, seems something else (courtesy of GRUB) is at play and I still have to boot from the other disk with GRUB bootloader on it.

Will fiddle with this more, and post back later (I only dabble in Vista occasionally, so it's not been a priority).

---

