---
title: "Acer 6292 - eRecovery Problems"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by craftomaniac on 2008-03-16
Hi there, I'm a total beginner to dual booting and all the other OS-es.

I'm using an Acer Travelmate 6292 and I followed the guide at:
[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)
I configured my partitions this way:
Acer's hidden partition: same size, 4gb or is it?
XP disk : 120GB (actually less i think)
and installed ubuntu on the remaining space.
However, after the installation, I can boot into Ubuntu perfectly (i'm using it to post here)
But I can't boot back into XP.
Whenever I try to do that, instead of Xp loading, it loads something called Acer eRecovery Management Environment and demands me to restore to factory defaults, restore from CD or exit. When I click exit it shuts down. What do I do?
I can still access my windows files, they're perfectly okay.
Has it got something to do with a ruined MBR and boot for XP?
Help, I really need to use XP.

---

### Post by Pumalite on 2008-03-16
If you are in Ubuntu as you say, post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by craftomaniac on 2008-03-16
Wow, that was fast.

sudo fdisk -lu

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x75cace1f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    10233404     5116671   12  Compaq diagnostics
/dev/sda2        10233405   244782404   117274500    7  HPFS/NTFS
/dev/sda3       244782405   309701069    32459332+  83  Linux
/dev/sda4       309701070   312576704     1437817+   5  Extended
/dev/sda5       309701133   312576704     1437786   82  Linux swap / Solaris

cat /boot/grub/menu.lst

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
# kopt=root=UUID=001663a1-68ef-4e3d-aaff-74a5ffd03d70 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=001663a1-68ef-4e3d-aaff-74a5ffd03d70 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=001663a1-68ef-4e3d-aaff-74a5ffd03d70 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows NT/2000/XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1

Thanks for replying.

---

### Post by craftomaniac on 2008-03-16
Wait a minute,

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows NT/2000/XP
root (hd0,0)
savedefault
makeactive
chainloader +1 

root (hd0, 0) ?! I'm guessing that refers to Acer's hidden partition?
If so, what do I change it to? root (hd0, 1) ?

---

### Post by Pumalite on 2008-03-16
Hidden partitions in laptops are a problem because Grub tends to install in them. We'll try:
Change this:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows NT/2000/XP
root (hd0,0)
savedefault
makeactive
chainloader +1 
To this:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows NT/2000/XP
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1 
Cross your fingers.

---

### Post by craftomaniac on 2008-03-16
Crossed my fingers, and uncrossed them immediately!

I don't know how to edit menu.lst yet (doubleclicked it in ubuntu's file explorer but couldn't save afterwards) so I just changed it (temporarily right?) from grub itself. Yes, booting to (hd0, 1) works. 
How do I change menu.lst for ever?

Thank you Pumalite for such a quick response! Can't thank you enough. Thank you, UbuntuForums community. Ubuntu rocks so far :guitar:. I'll probably be wine-ing lots of Windows apps.

---

### Post by Ace2016 on 2008-03-16
> **craftomaniac said:**
> Crossed my fingers, and uncrossed them immediately!

I don't know how to edit menu.lst yet (doubleclicked it in ubuntu's file explorer but couldn't save afterwards) so I just changed it (temporarily right?) from grub itself. Yes, booting to (hd0, 1) works. 
How do I change menu.lst for ever?

Thank you Pumalite for such a quick response! Can't thank you enough. Thank you, UbuntuForums community. Ubuntu rocks so far :guitar:. I'll probably be wine-ing lots of Windows apps.

sudo nano /boot/grub/menu.list

then make the changes, press Ctrl+X then it'll ask if you want to save changes or not, so press Y to save and then press enter, that should do it

just change root (hd0,0) to root (hd0,1) at the bottom, you can search by pressing Ctrl+W, so you could just search for root (hd0,0) to go directly there

---

### Post by craftomaniac on 2008-03-16
Thanks. It works. =)

---

### Post by Pumalite on 2008-03-16
Glad you got it working. Make a copy of menu.lst for future use:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old

---

### Post by craftomaniac on 2008-03-18
Okay. Thanks so much. :)

---

