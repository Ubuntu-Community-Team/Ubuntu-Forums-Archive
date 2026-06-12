---
title: "boot/Grub problems"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by pichagi on 2008-10-06
Hi Guys,

hope I'm not double posting(I have read a lot of threads).  I had a perfectly well working double booting system with windows xp and Ubuntu 8.04, but I just had to go a mess it all up...  For some reason, during the first installation of Ubuntu, at the partition stage, my system crashed so I ran the installer again and the installation worked fine.  I was then able to boot both Ubuntu and windows through Grub.  After some time, I've noticed in Windows that I had a 2nd partition that hadn't been created(this is probably the partition that was meant for Ubuntu during my 1st install until it crashed), so I made it into an NTFS partition. That did bother me since I just wanted 1 NTFS partition and not two, so I fired up Acronis Disk Manager and made 1 partition out of the two.  Problem is, by doing so I had to bring the last partion(NTFS) right after the the one that had Windows on it and bump my linux partition to the end of the hard drive.  Obviously, the first time I rebooted, Grub didn't work so after some reading I reinstalled Grub, but then I had an error 17 message saying that the partition coulnd't be found.  After reading again I changed (hd0,5) in my menu.lst file to (hd0,4).  I then rebooted again, this time had an error 22 message saying that there wasn't such thing as that partition.  

here is my fdisk-l:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdc47dc47

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4666    37479613+   7  HPFS/NTFS
/dev/sda2            4667        7296    21125475    5  Extended
/dev/sda5            4667        7181    20201706   83  Linux
/dev/sda6            7182        7296      923706   82  Linux swap / Solaris

here's my menu.lst:

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
# kopt=root=UUID=57c8059f-40b7-40c0-9925-6f301289ae28 ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=57c8059f-40b7-40c0-9925-6f301289ae28 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=57c8059f-40b7-40c0-9925-6f301289ae28 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


heres is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=57c8059f-40b7-40c0-9925-6f301289ae28 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=cfc1cb61-80fd-4907-b679-426c5d2d9aca none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


I really don't want to reinstall since I did install lots of software, tweaks and added many repositories.  Any help would be great, but please step by step since I'm still a noob to Linux and terminals.

Thanks

---

### Post by Pumalite on 2008-10-06
Do you see Grub? If you do; hit 'e' then 'e' again. Try (hd0,4), press 'Enter', then 'b' for boot. See if it works. You can try other combinations. When it works; you can edit your menu.lst to make it permanent.

---

### Post by pichagi on 2008-10-06
Wow!  That did it... The answer was right under my nose...  But why (hd0,4)???   I mean according to fdisk, shouldn't it be (hd0,2)?

---

### Post by Pumalite on 2008-10-06
Glad you got it working. Good luck!
(your Linux is in /dev/sda5. Grub starts counting from 0)
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
(sda3 does not exist)

---

### Post by pichagi on 2008-10-06
Oh, I see LOL!!!  I was counting them from top to bottom ((hd0,1),(hd0,2) ...). Thanks a lot for your precious help Pumalite, you're awesome.

---

