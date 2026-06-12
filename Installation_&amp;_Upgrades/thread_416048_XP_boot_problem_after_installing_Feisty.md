---
title: "XP boot problem after installing Feisty"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by gabng on 2007-04-20
Hi, since Fiesty was out, I decided to try it out on my desktop on a third harddisk.  Installation and everything went fine and I can boot into Ubuntu no problem.  However when I try to boot into XP, it stalls at a screen with just one line: "Starting up...".  This is after selecting XP from grub.

My desktop originally had 2 SATA harddisks, and I put back an unused ATA hd just to install Feisty on.  Below is my menu.lst and fstab

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
# kopt=root=UUID=633d80da-37b0-4bdf-a6de-17a9250c8f8e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=633d80da-37b0-4bdf-a6de-17a9250c8f8e ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=633d80da-37b0-4bdf-a6de-17a9250c8f8e ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=633d80da-37b0-4bdf-a6de-17a9250c8f8e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc3
UUID=983a773c-796c-4c03-8976-fb83fd704002 /home           ext3    defaults        0       2
# /dev/sda1
UUID=A890ECEF90ECC542 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=ACFC2505FC24CC00 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=F6243350243312DB /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=B4D83D69D83D2B4E /media/sda7     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=C8DC2123DC210D6E /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=D62CB2252CB20093 /media/sdb5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb6
UUID=2A78A58778A551FD /media/sdb6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc2
UUID=daf99e0a-ff49-4fb2-a2eb-6833b02dddf0 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

Ubuntu has no problem recognizing all my SATA drives, and I can read stuff off them in Ubuntu.  Can someone please help me out in getting XP able to start again?  Thanks in advance!

---

### Post by gabng on 2007-04-21
Anyone?

---

### Post by Smalls1652 on 2007-04-21
Hmmm, reinstall Windows XP, get files you need onto a flash drive or your ATA drive

---

### Post by gabng on 2007-04-21
Thanks for the input, but I feel that may be jumping to the last resort a little too soon.

I am suspecting the problem may lie in menu.lst, but I don't have enough knowledge to find out what is wrong with the XP entry (mapped to the wrong drive or partition maybe?).  I was hoping somebody more familiar with this can help me out.....

---

### Post by knob on 2007-04-21
Hi, I got the same problem...

I've Installed Ubuntu Feisty on my SATA Drive with the other ATA HD disconnected. Everything works fine.
Then I've connected the second HD (the ata one) and install Win Xp on it.

I've tried to insert these lines in my /boot/grub/menu.lst

title Windows
rootnoverify (hd1,0)
makeactive
chainloader +1
boot

But when I attempt to select Windows in the startup list,  it freezes at te "starting up..." message, and nothing happens...

Add info:   Ubuntu on SATA Drive seen as SCSI from my bios,  with GRUB on it,  booting ad working well.
                   Win XP on my ATA Drive, seen as Primary slave from my bios. If I set the bios startup from this disk, It works fine.

Can anyone help us????

---

### Post by jerrylamos on 2007-04-21
Traditionally, Microsoft always assumes it is the "first" partition on the "first" hard drive.  Period.

The Linux's will boot off other partitions and other hard drives, but my experience is they don't like to have the hard drive moved after the install.....

Cheers, Jerry

---

### Post by knob on 2007-04-21
Ok,  so there's a way to re-install GRUB on the ATA Disk, make it the default boot drive, then editing the menu to choose between Win XP and Ubuntu?

---

