---
title: "[SOLVED] Oops - Grub errors."
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by rax_m on 2007-11-14
Hi, 

I've had Ubuntu Feisty dual booting with Windows XP for almost a year now and everything has been fine. 
BUT .. I decided to install OpenSuse 10.3 on an external hdd today. Well, opensuse works fine. 

I then tried to reboot into Ubuntu, but unfortunately I'm getting errors. I think that there's somehow two versions of grub installed. One is the opensuse which shows first, then if I select ubuntu there it then shows me an Ubuntu (text) grub menu. However, choosing ubuntu the second time give me an error 18 ( i think). 
If I then reboot and unplug the external drive, I get a grub error 21. 

Here's the menu.lst from the opensuse install: 

```

# Modified by YaST2. Last modification on Wed Nov 14 18:23:02 SAST 2007
default 0
timeout 8
gfxmenu (hd1,1)/boot/message

###Don't change this comment - YaST2 identifier: Original name:  Ubuntu, kernel 2.6.20-16-generic (/dev/sda6)###
title Ubuntu, kernel 2.6.20-16-generic (/dev/sda6)
    root (hd0,5)
    configfile /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 10.3
    root (hd1,1)
    kernel /boot/vmlinuz-2.6.22.5-31-default root=/dev/disk/by-id/usb-WDC_WD40_0UE-22HCT0_DEF10A9EA88E-0:0-part2 vga=0x317 resume=/dev/sda7 splash=silent showopts
    initrd /boot/initrd-2.6.22.5-31-default

###Don't change this comment - YaST2 identifier: Original name: windows###
title Windows
    rootnoverify (hd1,1)
    chainloader (hd0,0)+1

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 10.3
    root (hd1,1)
    kernel /boot/vmlinuz-2.6.22.5-31-default root=/dev/disk/by-id/usb-WDC_WD40_0UE-22HCT0_DEF10A9EA88E-0:0-part2 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3
    initrd /boot/initrd-2.6.22.5-31-default

```

I'm not sure how to access the ubuntu install at the moment.. so can't get the menu.lst from there.. 

Please help :confused:

Thanks

---

### Post by rax_m on 2007-11-14
ok.. figured out how to mount the ubuntu partition.. here is the ubuntu menu.lst

```

# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=5a952c18-efac-498e-83e3-bda3a4bc6f90 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5a952c18-efac-498e-83e3-bda3a4bc6f90 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5a952c18-efac-498e-83e3-bda3a4bc6f90 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5a952c18-efac-498e-83e3-bda3a4bc6f90 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5a952c18-efac-498e-83e3-bda3a4bc6f90 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by rax_m on 2007-11-14
Hi. 

I'm trying to think this through on my own. In my mind, it seems to me that there is a grub install on hd0 (the original disk with windows and ubuntu) AND a grub install on hd1 (which I think is my external drive with opensuse). 

Opensuse seems to have a nice grub editor which can restore mbr's, and remove bootloaders etc. Do you think it's a that if use the remove boot loader option, it will remove the grub install from the external drive only. Then in theory everything should be fine right ???

---

### Post by rax_m on 2007-11-14
I managed to solve this with the Super Grub Disk that can be run as a livecd.. worked well after lots of reading ;)

---

