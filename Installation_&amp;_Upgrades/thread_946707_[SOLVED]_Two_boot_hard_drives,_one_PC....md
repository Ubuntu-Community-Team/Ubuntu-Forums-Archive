---
title: "[SOLVED] Two boot hard drives, one PC..."
date: 2008-10-13
forum: Installation &amp; Upgrades
---

### Post by daveybops on 2008-10-13
Here's an interesting one.

One house, three PCs; XP Home, Vista (hawk-ptooie) and Ubuntu.  However, when all three of us want to use Windows (very rare), we have to unplug the ubuntu hard drive from the PC and plug in the XP hard drive that the PC originally came with.  Is it possible that I can have both hard drives in the PC and configure a bootloader to select the OS to boot to without reloading either OS?

I thought about having the XP drive as the primary boot device and adding an instruction to the Windows boot.ini to tell it to boot off either, but I suspect that boot.ini only works on different flavours of Windows.

Any suggestions?

Cheers,

Dave

---

### Post by caljohnsmith on 2008-10-13
Sure, just set your BIOS to boot the Ubuntu drive, and you can add Windows as an option to boot from your Grub menu. How about first posting:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```
And let me know which partitions belong to which OS.

---

### Post by daveybops on 2008-10-13
ok, will give it a try. I am still a complete noob so although i have read a terminal tutorial or two, i still need a clearer idea of why i'm typing that command. I gather that the command will list hdd and partitions. i'll make ubuntu the primary master and windows the primary slave and odd on the secondary ide then boot ubuntu and report here the results of the command. Later. When i'm not tucked up in bed and responding to forum posts on my phone.

Thanks for the guidance so far.

---

### Post by daveybops on 2008-10-14
Done as suggested, attached the drive as primary slave and left the Ubuntu drive as primary master.  Then ran those two commands and here are the results.  Please bear in mind that I am one of those advanced Windows users (my job is basically to sort out hardware and software problems and nobody has ever come to our shop yet with a Linux PC) so I know a lot about MS and very little about Linux.

Notice how the Windows partition is FAT32 (might convert to NTFS sometime soon).

So now I have the two drives connected to the PC and I can browse the FAT32 partition.

dave@dave-desktop:~$ sudo fdisk -lu
[sudo] password for dave: 

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb586b586

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    77272649    38636293+  83  Linux
/dev/sda2        77272650    80292869     1510110    5  Extended
/dev/sda5        77272713    80292869     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0d9d0d9c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    78156224    39078081    c  W95 FAT32 (LBA)
dave@dave-desktop:~$ 
dave@dave-desktop:~$ 
dave@dave-desktop:~$ 
dave@dave-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=9140c8bb-2a22-4f78-9fdb-42139849ca5b ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9140c8bb-2a22-4f78-9fdb-42139849ca5b ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9140c8bb-2a22-4f78-9fdb-42139849ca5b ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by caljohnsmith on 2008-10-14
That's great, I think booting your Windows is probably going to be really easy. While you are in Ubuntu, open your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
And at the end of the file add:
```
title	   Windows XP
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Save, reboot, cross your fingers, say a few Linux mantras, and let me know what happens. :)

---

### Post by daveybops on 2008-10-16
Typed in: gksudo gedit /boot/grub/menu.lst

Entered p/w

Added thistothe textfile

title	   Windows XP
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

Saved.  Rebooted.  Crossed figers, muttered a prayer to Tux and hit the escape key. Found XP listed, selected, booted.

RESULT!

Many thanks.

---

### Post by caljohnsmith on 2008-10-16
That's great news, glad you can boot Windows now. Cheers and have fun. :)

---

