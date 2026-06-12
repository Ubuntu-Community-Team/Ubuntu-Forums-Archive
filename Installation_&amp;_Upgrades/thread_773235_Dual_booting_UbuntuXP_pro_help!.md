---
title: "Dual booting Ubuntu/XP pro help!"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by ieatfishburritos on 2008-04-28
Hello, I upgraded my wife's computer with hardy heron lts this weekend and let ubuntu create a 2nd partition to install itself.  

Upon reboot I get the correct options to select which OS, and Ubuntu works fine.  The issue is that XP pro will not load if it is selected.  I'm sure this is an easy one for some of you experts out there, but I'm a newb and need some help!



Selecting Windows from the boot menu results in this: 

Starting up ...
A disk read error occurred
Press Ctrl+Alt+Del to restart

Below is some of the common info I saw that others submitted with similar problems.  Thanks in advance for your help.

sudo fdisk -l

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000451b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15712   126206608+   7  HPFS/NTFS
/dev/sda2           19686       24792    41021977+  83  Linux
/dev/sda3           15713 
[16:24:48] Karine says: 
      19685    31913122+   5  Extended
/dev/sda5           15713       19516    30555598+  83  Linux
/dev/sda6           19517       19685     1357461   82  Linux swap / Solaris

Partition table entries are not in disk order


Menu.lst is below:

# menu.lst - See: grub(), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In
[16:24:20] Karine says: 
 this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu b
[16:24:20] Karine says: 
y default (press ESC to see the menu)
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
[16:24:20] Karine says: 


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
## by the debian update-grub script except for the default op
[16:24:20] Karine says: 
tions below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_
[16:24:20] Karine says: 
686=root=/dev/hdc2 ro
# kopt=root=UUID=9570ccc4-2d24-4adf-8072-f8807028ee26 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic bo
[16:24:20] Karine says: 
ot options
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

## Xen hypervisor options to
[16:24:20] Karine says: 
 use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the 
[16:24:20] Karine says: 
menu.lst
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

## should update
[16:24:20] Karine says: 
-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9570ccc4-2d24-4adf-8072-f8807028ee26 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(
[16:24:20] Karine says: 
hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9570ccc4-2d24-4adf-8072-f8807028ee26 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
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
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by damis648 on 2008-04-28
hmm... sounds like a GRUB issue as it claims "Starting Up..."
(i just deleted the last post i had not realised you already said what i asked for... sry :p)

---

### Post by Pumalite on 2008-04-28
Everything looks fine, except for this:
root (
[16:24:20] Karine says:
hd0,4)
in menu.lst
It should be:
root (hd0,4)
(I don't understand all the 'Karine' entries)

---

### Post by damis648 on 2008-04-28
hm ok i would try mounting the disk from ubuntu just goto the panel, Places>Computer and click on the partition (it might say the size or the name, IE "HP_PAVILION" or something...

---

### Post by ieatfishburritos on 2008-04-29
1st off, sorry for all of the "Karine says" comments in there, please ignore those as they are a byproduct of sending these files over chat!

I didn't mention that in Ubuntu I can mount the windows partition without a hitch. So it's there.  It just shows up as "129 Gb Media".

I went and changed the following section in the menu.lst:

From
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1 

to root (hd0,4) as recommended.  It didn't work and upon selecting xp it gives an error about an invalid device.  For the record I also tried (hd0,1), (hd0,2) and (hd0,3) and they didnt work either..

I need more help on this please!

---

### Post by housam on 2008-04-29
Maybe your MBR is corrupted , try to fix it using the [[COLOR="Red"]_super Grub disk_[/COLOR]]("http://supergrub.forjamari.linex.org/")

---

