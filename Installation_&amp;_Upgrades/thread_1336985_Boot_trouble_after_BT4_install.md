---
title: "Boot trouble after BT4 install"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by Jemain on 2009-11-25
Hello people,  My computer had Ubuntu 9.1 Karmic on it until recently, when I installed BT4 on an external USB HDD. Now the BT4 install has overwritten the Karmic Grub2 with it's own Grub. There are still entries in the menu.lst for karmic, but when I choose them it gives me the error:

```
Error 15: File not found
```Could anyone please help me fix this, I really like Karmic and don't want to loose all my work I did on the distribution. Thx


(In the menu.list i've tried the following for the karmic entries: change the HD to (0,1) and (1,0), removed the /boot before the kernel obviously none of this worked as I'm here asking. My guess is that Karmic and BT4 both have an other way of &quot;naming&quot; my HDDs and this gives conflict on boot? hope someone can help)

here's what the menu.lst looks like:

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
# kopt=root=UUID=fa1ea273-8879-484f-97e9-ad8626421bdb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=fa1ea273-8879-484f-97e9-ad8626421bdb

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
## e.g. defoptions=vga=0x317 resume=/dev/hda5
# defoptions=vga=0x317

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

splashimage=/boot/grub/splashimages/gentleblue.xpm.gz

title        Ubuntu 8.10, kernel 2.6.29.4
uuid        fa1ea273-8879-484f-97e9-ad8626421bdb
kernel        /boot/vmlinuz-2.6.29.4 root=UUID=fa1ea273-8879-484f-97e9-ad8626421bdb ro vga=0x317 
initrd        /boot/initrd.img-2.6.29.4
quiet

title        Ubuntu 8.10, kernel 2.6.29.4 (recovery mode)
uuid        fa1ea273-8879-484f-97e9-ad8626421bdb
kernel        /boot/vmlinuz-2.6.29.4 root=UUID=fa1ea273-8879-484f-97e9-ad8626421bdb ro  single
initrd        /boot/initrd.img-2.6.29.4

title        Ubuntu 8.10, memtest86+
uuid        fa1ea273-8879-484f-97e9-ad8626421bdb
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu, Linux 2.6.31-15-generic (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=b630ab0a-9c51-46fa-87fe-acf8fb867830 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu, Linux 2.6.31-15-generic (recovery mode) (on /dev/sda1)
root        (hd0,0)
kernel        /vmlinuz-2.6.31-15-generic root=UUID=b630ab0a-9c51-46fa-87fe-acf8fb867830 ro single 
initrd        /initrd.img-2.6.31-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu, Linux 2.6.31-14-generic (on /dev/sda1)
root        (hd0,0)
kernel        /vmlinuz-2.6.31-14-generic root=UUID=b630ab0a-9c51-46fa-87fe-acf8fb867830 ro quiet splash 
initrd        /initrd.img-2.6.31-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda1)
root        (hd0,0)
kernel        /vmlinuz-2.6.31-14-generic root=UUID=b630ab0a-9c51-46fa-87fe-acf8fb867830 ro single 
initrd        /initrd.img-2.6.31-14-generic
savedefault
boot

```

---

### Post by Jemain on 2009-11-26
Hi again people,

In the mean time I have changed some things, I've updated to GRUB2, which seems to recognise Ubuntu 9.1 better. But still doesn't boot.
Now when I want to boot Ubuntu 9.10 it says 

"Error: need to load kernel first"

this is the relevant piece from grub.cfg:

```
### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, linux 2.6.29.4" {
    linux    (hd1,1)/boot/vmlinuz-2.6.29.4 root=UUID=fa1ea273-8879-484f-97e9-ad8626421bdb ro quiet splash 
    initrd    (hd1,1)/boot/initrd.img-2.6.29.4
}
menuentry "Ubuntu, linux 2.6.29.4 (single-user mode)" {
    linux    (hd1,1)/boot/vmlinuz-2.6.29.4 root=UUID=fa1ea273-8879-484f-97e9-ad8626421bdb ro single
    initrd    (hd1,1)/boot/initrd.img-2.6.29.4
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux    (hd1,1)/boot/memtest86+.bin
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, Linux 2.6.31-15-generic (on /dev/sda1)" {
    set root=(hd0,1)
    linux /boot/vmlinuz-2.6.31-15-generic root=UUID=UUID_of_sda1 ro quiet splash
    initrd initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode) (on /dev/sda1)" {
    set root=(hd0,1)
    linux /boot/vmlinuz-2.6.31-15-generic root=UUID=b630ab0a-9c51-46fa-87fe-acf8fb867830 ro single
    initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda1)" {
    set root=(hd0,1)
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=b630ab0a-9c51-46fa-87fe-acf8fb867830 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda1)" {
    set root=(hd0,1)
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=b630ab0a-9c51-46fa-87fe-acf8fb867830 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###
```

As you can see I've tried changing the "root=UUID=blablablablabla" into "root=UUID=UUID_of_sda1" but this gives the same result.

Th thing I think is the problem, is that my (hd0,1) is my boot partition, but that gets loaded is on my (hd1,1) disk. how can I install grub back on my Ubuntu 9.1 disk?

Maybe the best help would be, how can I boot 9.1 from the GRUB commandline?

Thx for alll your replies...

---

