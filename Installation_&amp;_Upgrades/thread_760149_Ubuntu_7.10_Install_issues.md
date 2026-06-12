---
title: "Ubuntu 7.10 Install issues"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by ladysun1 on 2008-04-19
Installed Ubuntu on my Vista machine and could not access it through GRUB.  Kept getting the "Error 17" message about not being able to mount it.   I have searched through this forum and have tried all the solutions to this and could not fix it so I decided to try the "F8" function to see if the location I wanted to install it on the HD was correct and that worked (I have 4 HDDs and Linux is on a 13GB one) but the program stalled at the "Ubuntu" progress bar screen.  Then after two minutes or so I received another black screen with Debian at the top header and below some cryptic error message about a "box"?:confused:   Sorry about how vague this request is but I have been trying to get this to work all afternoon......:(

Help!

---

### Post by Pumalite on 2008-04-19
Boot your Live CD. From the Terminal, post:
sudo fdisk -l

---

### Post by ladysun1 on 2008-04-19
Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05ab05ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24791   199133676    7  HPFS/NTFS

Disk /dev/sdb: 13.0 GB, 13030907904 bytes
255 heads, 63 sectors/track, 1584 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12d612d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1511    12137076   83  Linux
/dev/sdb2            1512        1584      586372+   5  Extended
/dev/sdb5            1512        1584      586341   82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1           5       40131   de  Dell Utility
/dev/sdc2   *           6       19093   153324360    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9f8e1613

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sde: 250 MB, 250640384 bytes
8 heads, 60 sectors/track, 1019 cylinders
Units = cylinders of 480 * 512 = 245760 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   ?     1621117     3999262   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(1621116, 3, 49)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(3999261, 4, 19)
Partition 1 does not end on cylinder boundary.
/dev/sde2   ?      351437     4384829   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(351436, 4, 3)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(4384828, 5, 22)
Partition 2 does not end on cylinder boundary.
/dev/sde3   ?     3895587     7928979   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(3895586, 3, 6)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(7928978, 3, 37)
Partition 3 does not end on cylinder boundary.
/dev/sde4   ?     6011836     6011952       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(6011835, 5, 53)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(6011951, 2, 51)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
ubuntu@ubuntu:~$

---

### Post by Pumalite on 2008-04-19
You have a problem with sde, but will leave that for later. Mount the partition:
sudo mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
Post:
cat /media/sdb1/boot/grub/menu.lst

---

### Post by ladysun1 on 2008-04-19
Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sdb1 /media/sdb1
mount: mount point /media/sdb1 does not exist
ubuntu@ubuntu:~$ cat /media/sdb1/boot/grub/menu.lst
cat: /media/sdb1/boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ 
:(

---

### Post by Pumalite on 2008-04-19
You forgot this:

sudo mkdir /media/sdb1

---

### Post by ladysun1 on 2008-04-19
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
# kopt=root=UUID=0efa59b6-0452-464a-b1b5-219cb9e45ab5 ro
# kopt_2_6=root=/dev/hda1 ro

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc2
title           Windows Vista/Longhorn (loader)
root            (hd2,1)
savedefault
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1

ubuntu@ubuntu:~$ 

:confused:

---

### Post by ladysun1 on 2008-04-19
I didn't enter those smileys ----- it's supposed to be (the number eight)s:lolflag:

---

### Post by Pumalite on 2008-04-19
I assume you have gedit in your Live CD (not sure)
Edit:
gksudo gedit /media/sdb1/boot/grub/menu.lst
Change Ubuntu's 'root' line to (hd1,0)
Save, exit.
Let's see if Ubuntu boots first.

---

### Post by Pumalite on 2008-04-19
I'll be back tomorrow 8 AM Eastern Time. Cheers

---

### Post by ladysun1 on 2008-04-19
Hope this works and will let you know tomorrow AM!

---

### Post by ladysun1 on 2008-04-19
Thanks! :)

---

### Post by ladysun1 on 2008-04-19
:KS GRUB worked but with errors.  The Ubuntu splash screen comes up but nothing loads (progress bar stuck)

After a couple of minutes, the BusyBox screen appears with a command line: initramfs:(

I think I may have to update a file?  Would you be able to send me the commands to do this

and will I have to use the Live CD again?

---

### Post by Pumalite on 2008-04-20
Post your new menu.lst.

---

### Post by ladysun1 on 2008-04-20
:confused:  [COLOR="Purple"]**Sorry, would you tell me what command to use to get to that menu?  I feel so embarrassed.... :([/COLOR]**

---

### Post by Pumalite on 2008-04-20
You have to boot your Live CD. Mount your partition. Then:
cat /media/sdb1/boot/grub/menu.lst

---

### Post by ladysun1 on 2008-04-20
menu.lst - See: grub(8), info grub, update-grub(8)
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
# root          (hd1,0)
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
# kopt=root=UUID=0efa59b6-0452-464a-b1b5-219cb9e45ab5 ro
# kopt_2_6=root=/dev/hda1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd1,0)
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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,0)
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc2
title           Windows Vista/Longhorn (loader)
root            (hd2,1)
savedefault
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1

ubuntu@ubuntu:~$

---

### Post by Pumalite on 2008-04-20
Your working Vista is in sda1, right?

---

### Post by ladysun1 on 2008-04-20
Yes, that is correct and that sde problem you mentioned last evening belongs to my Iomega  USB external disc (250MB)

---

### Post by Pumalite on 2008-04-20
OK. Change this:

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista/Longhorn (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc2
title Windows Vista/Longhorn (loader)
root (hd2,1)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

To this:

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista/Longhorn (loader)
rootnoverify (hd0,0)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
savedefault
makeactive
chainloader +1

Save, exit and reboot.

---

### Post by ladysun1 on 2008-04-20
No, that did not work.   Still not loading Ubuntu.........

---

### Post by Pumalite on 2008-04-20
Sorry, I ran out of answers. According to your fdisk and menu.lst; both Vista and Ubuntu should be booting by now. Someone wiser will come along.Are both your drives SATA or both IDE or are they a mix? If they are a mix, beware of this:
[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)

---

### Post by ladysun1 on 2008-04-20
Yes, they are a mix.   I have one SATA, 3 externals and 2 IDEs

The externals are not on all the time.   I did notice in my GRUB loader than an extra entry for Windows Vista loader was removed.

I am replying to you from within the Vista OS and both loaders are listed correctly..........

Thanks for the links.   I will see if the suggestions there will work for the Ubuntu loading.

---

### Post by Pumalite on 2008-04-20
I have to advice you to install both OS's in the first drive (sda?) and keep the others for storage. That's the problem we've been experimenting.

---

### Post by ladysun1 on 2008-04-20
I was trying to give Linux its own dedicated drive which is not SATA controlled. (13GB)

My Vista OS is on a SATA drive (160GB) and over half capacity is used already

I have a 200GB storage IDE with just Vista programs no OS and I would like to leave it that way


Ideally, I would like to install the Linux and the SWAP on that 13GB.  


Now you tell me it is impossible?  Can both OSes exist in different partitions on the same drive?

Please bump if this is the incorrect forum :???::???::-#:-#

---

### Post by Pumalite on 2008-04-20
I would install Ubuntu where Vista is. Partition with Vista partitioner to 'free space' for Ubuntu. If the partition is small, it doesn't matter you can have a /home in a different drive. If you want a different opinion start a new thread along the lines of 'Installing in 2 HDD Mix of SATA and IDE'

---

