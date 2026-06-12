---
title: "[SOLVED] Triple booting"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by z|x on 2008-05-12
Here's the situation:

I have an HP laptop. It came with Vista preinstalled. I made a partition on the drive and installed Kubuntu but the free space on Kubuntu's partition is almost over.
So, I had another IDE drive. I connected it via USB and installed Kubuntu on that too. So now, when I boot up, I get options for Kubuntu on the External HD, and Kubuntu and Vista on the laptop's HD.

Is there a way to make my laptop load into Vista or Kubuntu (on my laptop's HD) if my External Drive is not connected? Right now, if my external drive is disconnected, GRUB gives me an error.

Any help is appreciated.

Thanks.

---

### Post by logos34 on 2008-05-12
Boot into kubuntu on the main drive and reinstall grub to mbr:

sudo grub-install /dev/sda (or hda)

-add a [symlink]("http://users.bigpond.net.au/hermanzone/p15.htm#3._Symlink") entry for the usb kubuntu installation to /boot/grub/menu.lst

---

### Post by z|x on 2008-05-12
> **logos34 said:**
> Boot into kubuntu on the main drive and reinstall grub to mbr:

sudo grub-install /dev/sda (or hda)

-add a [symlink]("http://users.bigpond.net.au/hermanzone/p15.htm#3._Symlink") entry for the usb kubuntu installation to /boot/grub/menu.lst
Just to make sure, main drive would be my laptop drive right?

---

### Post by logos34 on 2008-05-12
> **z|x said:**
> Just to make sure, main drive would be my laptop drive right?

yes

---

### Post by z|x on 2008-05-12
I would like to make one thing clear.

I want my laptop to boot up normally without the ext hd. that is, it should give me an option to boot into kubuntu or vista. And when my ext hd is connected, I want it to give me an option to boot into the kubuntu installed on the ext hd.

Thanks

---

### Post by z|x on 2008-05-12
> **logos34 said:**
> yes
Could you explain a bit more as to how I'm supposed to work it out? I'm a real noob at all this booting stuff.

---

### Post by logos34 on 2008-05-12
Basically you're just restoring the original kubuntu grub (stage1) to the mbr, pointing to menu.lst on the root partition on the internal drive.

Then you have to add an entry for the usb kubuntu installation to menu.lst.  So, for example if the latter is on the first partition, you would do:

sudo nano /boot/grub/menu.lst

now add symlink

> 
title        Kubuntu 8.04 
root         (hd1,0) 
kernel       /vmlinuz root=/dev/sdb1 ro quiet splash
initrd       /initrd.img

I forgot to ask: why two separate kubuntu installations?  Or do you want to delete the one on the internal and have just vista there and kubuntu on the usb?  If the latter, you'll have to create a small **dedicated grub partition** (see grub page link above) on the internal to hold menu.lst, or else use EasyBCD to allow you to use vista bootloader to boot linux

Oh, and you;ll need to edit menu.lst on the usb kubuntu install so 'root' and 'groot' lines read (hd**1**,0) -- again, assuming its the first partition

---

### Post by z|x on 2008-05-12
These are the contents of my menu.lst file currently:

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

#A splash image for the menu
#splashimage=(hd0,3)/boot/grub/splashimages/60589-gnulinux.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=1eefd331-9a2d-414a-87f6-d54f5d5e995d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
# defoptions=vga=791 quiet splash

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
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1eefd331-9a2d-414a-87f6-d54f5d5e995d ro vga=791 quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1eefd331-9a2d-414a-87f6-d54f5d5e995d ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=1eefd331-9a2d-414a-87f6-d54f5d5e995d ro vga=791 quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=1eefd331-9a2d-414a-87f6-d54f5d5e995d ro single
initrd		/boot/initrd.img-2.6.22-14-generic

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
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


```

---

### Post by z|x on 2008-05-12
> **logos34 said:**
> Basically you're just restoring the original kubuntu grub (stage1) to the mbr, pointing to menu.lst on the root partition on the internal drive.

Then you have to add an entry for the usb kubuntu installation to menu.lst.  So, for example if the latter is on the first partition, you would do:

sudo nano /boot/grub/menu.lst

now add symlink



I forgot to ask: why two separate kubuntu installations?  Or do you want to delete the one on the internal and have just vista there and kubuntu on the usb?  If the latter, you'll have to create a small **dedicated grub partition** (see grub page link above) on the internal to hold menu.lst, or else use EasyBCD to allow you to use vista bootloader to boot linux

Oh, and you;ll need to edit menu.lst on the usb kubuntu install so 'root' and 'groot' lines read (hd**1**,0) -- again, assuming its the first partition
I dont have enough of space on my partition for kubuntu. So, I use it only for my important work and the software installed on it is very limited. So, now that I have an external hd, i can experiment with other stuff...

---

### Post by z|x on 2008-05-13
> **logos34 said:**
> Basically you're just restoring the original kubuntu grub (stage1) to the mbr, pointing to menu.lst on the root partition on the internal drive.

Then you have to add an entry for the usb kubuntu installation to menu.lst.  So, for example if the latter is on the first partition, you would do:

sudo nano /boot/grub/menu.lst

now add symlink



I forgot to ask: why two separate kubuntu installations?  Or do you want to delete the one on the internal and have just vista there and kubuntu on the usb?  If the latter, you'll have to create a small **dedicated grub partition** (see grub page link above) on the internal to hold menu.lst, or else use EasyBCD to allow you to use vista bootloader to boot linux

Oh, and you;ll need to edit menu.lst on the usb kubuntu install so 'root' and 'groot' lines read (hd**1**,0) -- again, assuming its the first partition
I entered the code but when I boot up into the Kubuntu on the ext hd, it shows the loading screen of Kubuntu and then it takes me to BusyBox.

This is what my menu.lst looks like:

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

#A splash image for the menu
#splashimage=(hd0,3)/boot/grub/splashimages/60589-gnulinux.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=1eefd331-9a2d-414a-87f6-d54f5d5e995d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
# defoptions=vga=791 quiet splash

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
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=1eefd331-9a2d-414a-87f6-d54f5d5e995d ro vga=791 quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=1eefd331-9a2d-414a-87f6-d54f5d5e995d ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title Kubuntu 8.04 - External
root (hd1,2)
kernel /vmlinuz root=/dev/sdb1 ro quiet splash
initrd /initrd.img 

title        Ubuntu 8.04, kernel 2.6.22-14-generic
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=1eefd331-9a2d-414a-87f6-d54f5d5e995d ro vga=791 quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=1eefd331-9a2d-414a-87f6-d54f5d5e995d ro single
initrd        /boot/initrd.img-2.6.22-14-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista/Longhorn (loader)
root        (hd0,1)
savedefault
makeactive
chainloader    +1


```

And this is the entry for booting up into kubuntu (ext hd) taken from that hd:

```
title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd1,2)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=6e797bd0-cf8f-433b-8efe-0991f7ff39a3 ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet
```

---

### Post by z|x on 2008-05-13
Ok, I got it working. Thanks for the help [logos34]("http://ubuntuforums.org/member.php?u=127804")!!

---

### Post by logos34 on 2008-05-13
> **z|x said:**
> Ok, I got it working. Thanks for the help [logos34]("http://ubuntuforums.org/member.php?u=127804")!!

So no more busybox error? 

I encourage you to use either the symlink or configfile menu.lst entry, because otherwise you will have a problem after the next kernel update.


> title Kubuntu 8.04
root (hd1,2)
kernel /vmlinuz root=UUID=6e797bd0-cf8f-433b-8efe-0991f7ff39a3 ro quiet splash
initrd /initrd.img

(Or instead of UUID use **root=/dev/sdb3**)

OR

> title       Kubuntu Configfile Boot
configfile  (hd1,2)/boot/grub/menu.lst

Enjoy ubuntu!

---

### Post by z|x on 2008-05-13
oh ok, thanks. How often do we have kernel upgrades? is it only when the next version of ubuntu will be released?

---

### Post by logos34 on 2008-05-13
there's usually at least one kernel update between releases

---

### Post by z|x on 2008-05-13
ok

---

