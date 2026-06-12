---
title: "Wrong choices"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by ianrb001 on 2008-05-26
Hi. I have just upgraded from 7.10 to 8.04 but I have made a mistake somewhere along the line. It still loads 7.10 in very low graphics resolution. I was asked several times during the installation if I wanted to keep certain settings and I said yes. I think this was a mistake. What do I need to put in the Grub menu.lst to make it start with 8.04? 

With thanks.

Ian :)

---

### Post by iaculallad on 2008-05-26
> **ianrb001 said:**
> Hi. I have just upgraded from 7.10 to 8.04 but I have made a mistake somewhere along the line. It still loads 7.10 in very low graphics resolution. I was asked several times during the installation if I wanted to keep certain settings and I said yes. I think this was a mistake. What do I need to put in the Grub menu.lst to make it start with 8.04? 

With thanks.

Ian :)

Post your /boot/grub/menu.lst

Code:

> cat /boot/grub/menu.lst

---

### Post by ianrb001 on 2008-05-28
Hi. Thanks for taking an interest. Here is the Grub menu.lst:). There are other things wrong also but I'm picking that they will probably come right if this problem is sorted out.

With thanks.

Ian :popcorn:

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and # the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry # is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' 
or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry # (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu) #hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing # control (menu entry editor and command-line)  and entries protected by the # command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
## lines between the AUTOMAGIC KERNELS LIST markers will be modified ## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options ## If you want special options for specific kernels use kopt_x_y_z ## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e679f110-11b4-4eb3-ae0d-7828a034c2bb ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options ## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options ## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the ## alternatives ## e.g. defoptions=vga=791 resume=/dev/hda5 # defoptions=quiet splash

## should update-grub lock old automagic boot options ## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option # xenhopt=

## Xen Linux kernel options to use with the default Xen boot option # xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed ## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst ## only counts the first occurence of a kernel, not the ## alternative kernel options ## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option ## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system ## can be true or false # updatedefaultentry=false

## should update-grub add savedefault to the default options ## can be true or false # savedefault=false

## ## End Default Options ##
#
# This entry automatically added by the Debian installer for a non-linux OS # on /dev/hda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1


title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.22-14-generic 
root=UUID=e679f110-11b4-4eb3-ae0d-7828a034c2bb ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.22-14-generic 
root=UUID=e679f110-11b4-4eb3-ae0d-7828a034c2bb ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, kernel 2.6.20-16-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.20-16-generic 
root=UUID=e679f110-11b4-4eb3-ae0d-7828a034c2bb ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet

title        Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.20-16-generic 
root=UUID=e679f110-11b4-4eb3-ae0d-7828a034c2bb ro single
initrd        /boot/initrd.img-2.6.20-16-generic

title        Ubuntu 7.10, memtest86+
root        (hd1,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian # ones.
# title        Other operating systems:
# root


# This entry automatically added by the Debian installer for a non-linux OS # on /dev/hda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1

# This entry automatically added by the Debian installer for a non-linux OS # on /dev/hda1
# title        Microsoft Windows XP Home Edition
# root        (hd0,0)
# savedefault
# makeactive
# chainloader    +1

---

### Post by iaculallad on 2008-05-28
It seems that you only have Gutsy on your GRUB menu list with no traces of Hardy. On what partition did you actually install your Hardy?

Check this [link]("http://www.ubuntugeek.com/upgrade-ubuntu-710-gutsy-gibbon-to-ubuntu-804-lts-hardy-heron-beta.html") and compare your procedure on upgrading.

---

### Post by ianrb001 on 2008-05-28
Hi

I installed from 7.10 via the upgrade button on the ubuntu site. I have now downloaded Hardy from t Ubuntu at work (much faster connection) and will save the image to DVD and try to upgrade again, unless you percieve there is a problem with this.

With thanks.

Ian

---

### Post by iaculallad on 2008-05-28
You could try upgrading again, only this time, see to it that you follow the instruction on the site I linked above. Goodluck.

PS. I suggest you do a clean install on Hardy if you plan on upgrading it again. This will ensure that no problems regarding installation will pop in the future. 
You can do your clean install but do backup your important files first.

---

