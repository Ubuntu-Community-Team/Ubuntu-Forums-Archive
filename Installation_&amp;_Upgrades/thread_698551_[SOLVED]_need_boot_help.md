---
title: "[SOLVED] need boot help"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by rico4295 on 2008-02-16
I've installed gutsy onto my boot drive(sata). I had the install repartition the xp part leaving 30gig of 120 to install gutsy. After reading and fixing the menu.lst it will boot gutsy fine now.  The trouble is I can't get xp to boot. I've 'e' at the boot menu and changed it to hd0,0 , this gets rid of the error but doesn't load xp it just scrolls garbage. I hope i'm getting closer.
tia
rico

---

### Post by sandysandy on 2008-02-16
> **rico4295 said:**
> I've installed gutsy onto my boot drive(sata). I had the install repartition the xp part leaving 30gig of 120 to install gutsy. After reading and fixing the menu.lst it will boot gutsy fine now.  The trouble is I can't get xp to boot. I've 'e' at the boot menu and changed it to hd0,0 , this gets rid of the error but doesn't load xp it just scrolls garbage. I hope i'm getting closer.
tia
rico

have a look at this link of dual boot

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

regards

---

### Post by Pumalite on 2008-02-16
Edit your menu.lst and add Windows at the end (there is a sample in the menu.lst on how to do it). Backup your file first.

---

### Post by rico4295 on 2008-02-16
the grub boot menu has the xp option but it gives error 12. If i edit it to hd0,0 it does
Starting up ...
garbage,garbage.....

I looked the to link sandysandy gave and tried to edit the boot.ini but no luck yet

---

### Post by Pumalite on 2008-02-16
Post:
sudo fdisk -lu

---

### Post by rico4295 on 2008-02-16
Disk /dev/hdb: 27.3 GB, 27373731840 bytes
255 heads, 63 sectors/track, 3328 cylinders, total 53464320 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb08ae147

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *       16065    53464319    26724127+   f  W95 Ext'd (LBA)
/dev/hdb5           16128    53464319    26724096    b  W95 FAT32

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x27c927c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   167766794    83883366    7  HPFS/NTFS
/dev/sda2       167766795   231593039    31913122+  83  Linux
/dev/sda3       231593040   234436544     1421752+   5  Extended
/dev/sda5       231593103   234436544     1421721   82  Linux swap / Solaris


these are reversed becaude I edied the device.map and changed it back but haven't rebooted yet

---

### Post by Pumalite on 2008-02-16
What's the boot order of your drives in BIOS?

---

### Post by rico4295 on 2008-02-16
I haven't changed it in bios. boot order is cdrom, sata 120gig, ide 27 gig

---

### Post by Pumalite on 2008-02-16
Post:
cat /boot/grub/menu.lst

---

### Post by rico4295 on 2008-02-16
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
# kopt=root=UUID=e6029586-35e7-435c-a5b9-838bdea8606c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=e6029586-35e7-435c-a5b9-838bdea8606c ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=e6029586-35e7-435c-a5b9-838bdea8606c ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (h0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

---

### Post by Pumalite on 2008-02-16
Change this:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

TO THIS:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

Save and reboot.

---

### Post by rico4295 on 2008-02-16
ok now after choosing the xp option it goes to
Starting up ...
scrolling garbage....

---

### Post by Pumalite on 2008-02-16
Then you have the old IDE+SATA problem. Here are some links:
[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)

You can also Google the problem. You'll get lots of hits.

---

### Post by rico4295 on 2008-02-16
I'll do some more reading and thank you for your time
rico

---

### Post by rico4295 on 2008-02-16
After reading about the grub commands and learing that the map commands trick xp's boot loader into pointing in the right location. I tried this..
In the terminal~>gksudo gedit /boot/grub/menu.lst and edited the follwing lines at the bottom
# map (hd0) (hd1)
# map (hd1) (hd0)
By commenting out the map commands xp now loads up, Mark as Solved. Hope this helps others.
Thanks again
rico

---

### Post by Pumalite on 2008-02-16
Congrats. Sorry I missed that.

---

