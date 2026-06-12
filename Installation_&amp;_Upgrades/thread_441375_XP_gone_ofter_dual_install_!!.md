---
title: "XP gone ofter dual install !!"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by iiyama on 2007-05-12
Hi 

I recently installed feisty on my laptop dual booting with vist. I liked an decided to dual boot with my home PC (dell dimensions xps) now i con not boot to windows.

My setup:

2 x 160 GB hard drives (sata1 and sata3) setup as raid 0 ----showin in Windows xp as one 320 gb HD. Win xp system is installed on this drive.

1 x 250 gb HD (sata1). showed as a separate hard drive in windows xp . This drive was partitioned in half.  Ubuntu feisty was in stalled on a 130gb partition of this drive with a 1 gb swap. The remainder of the drive was left as ntfs format. 

After installation Ubuntu works fine. 

Problem:
I cannot find the option to boot to xp in the grub menu.  There ore only three entries all of which are for Ubuntu. 

I also noticed during installation that Ubuntu partition manager did not recognized my raid 0 configuration. The drives were shown separate (2 x 160gb) rather than one large drive. However I did not change these drives in any way during the installation. 

I would appreciate any help to allow window  to boot. 
thank you

---

### Post by confused57 on 2007-05-12
I'm not familiar with a Raid configuration, but you might post the output of:
```
gedit /boot/grub/menu.lst
gedit /boot/grub/device.map
```

and

```
sudo fdisk -l
```
the -l is a lowercase "L"

---

### Post by iiyama on 2007-05-12
Hi confused57

output from : gedit /boot/grub/menu.lst
gedit /boot/grub/device.map


> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=18b545e0-bfc4-4048-a6ec-0a271bc7e731 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,5)

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=18b545e0-bfc4-4048-a6ec-0a271bc7e731 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)


Output from sudo fdisk -l is:

> Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2   *          10       38902   312408022+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *           2       30401   244188000    5  Extended
/dev/sdb5               2       14361   115346668+   7  HPFS/NTFS
/dev/sdb6           14362       30279   127861303+  83  Linux
/dev/sdb7           30280       30401      979933+  82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdc doesn't contain a valid partition table

hope that helps

---

### Post by confused57 on 2007-05-12
Since I don't use a Raid configuration, I'm not sure what might work for you...here's some info on installing on a Raid array:
[https://help.ubuntu.com/community/Installation#head-86a18ab57715d9bb5f0dfaba497a928e67cd73ed](https://help.ubuntu.com/community/Installation#head-86a18ab57715d9bb5f0dfaba497a928e67cd73ed)

It probably won't work, but you could try adding a Window's entry to your menu.lst:
```
title              Windows XP
rootnoverify       (hd0,0)
savedefault
makeactive
chainloader        +1
```

You can always reinstall Window's IPL code to the mbr, in order to boot Windows:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

This is pure speculation on my part, but my thinking is your setup may have  worked if you selected your 250 Gb hard drive as the first hard drive booted in bios, then your sda & sdb next, when you installed  Ubuntu.  Booting first to the 250 Gb hard drive may allow you to boot the Raid configuration from grub?  
You might want to start a new thread with setting up Ubuntu on a Raid configuration, this might catch the eye of someone experienced in this area.

---

### Post by iiyama on 2007-05-13
hi

thanks confused57.

i used the instructions in your link:

> [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)


to load windows by using the command: fixmbr in the recover module 
win xp loads fine now! :popcorn: 

but how do i load Ubuntu now. I cant seem to load grub any more??

cheers:guitar:

---

### Post by confused57 on 2007-05-13
The command fixmbr overwrote your grub on your boot drive mbr...I'm not sure with your Raid configuration that grub will boot your Windows being installed to the first Raid hard drive mbr.  Not being familiar with Raid, I thought you might try installing grub to your Ubuntu drive mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
The link explains it very well, but you'll need to open a terminal:
```
sudo grub
find /boot/grub/stage1
```
this will return "root (hdx,y)", to install grub to your Ubuntu drive's mbr:
```
root (hdx,y)
setup (hdx)
quit
```

Then go into bios and set your Ubuntu drive as the first hard drive in your boot sequence, you should get a grub menu, highlight your Ubuntu entry, press "e", change root from (hdx,y) to (hd0,y), then press "b" to boot...if this works, it's only temporary, but it can be made permanent in your /boot/grub/menu.lst.

---

### Post by darwid on 2007-05-15
I have the exact same problem as you and pretty much the same configuration.

Basically, I initially have windows XP installed on two SATA drives (/sda,/sdb) configured as RAID0 from the Bios (nVidia).
I put a 3rd drive in my computer (/sdc) and this one is just a regular SATA drive and I installed Ubuntu on it.

During install the 2 other drives showed as single drive rather than a RAID array but I left them untouched anyway since I was installing to /sdc

Now, I can't boot windows since Grub doesn't offer this option. I know I can fix this by doing a fixmbr (but then I wouldn't be able to boot Ubuntu ;))

I saw somewhere while browsing that Grub doesn't support RAID while Lilo does, I tried to find some tutorial on lilo and RAID without much luck.

Does anyone know about this ?

---

### Post by heartbeat on 2007-05-16
I've got the same problem.
Windows is no longer an option in the GRUB menu.

there are just a couple of things i still want to use in windows.

---

### Post by Soybean on 2007-05-16
Well, since the Windows bootloader is obviously happy with the RAID drives, while grub might take some extra convincing... why not just use the Windows bootloader to pick your OS instead of grub?

I think this thread might help in that regard: [http://ubuntuforums.org/showthread.php?t=56723](http://ubuntuforums.org/showthread.php?t=56723)

---

