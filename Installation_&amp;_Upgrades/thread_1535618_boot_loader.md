---
title: "boot loader"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by aliboy on 2010-07-21
need help edit boot loader to boot windows OS first and edit waiting time also. 

here is the menu.lst



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

## debug [on | off | normal | status | INTEGER]
# Turn on/off or display/set the debug level.
debug		off

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
# kopt=root=UUID=735761e0-a79d-469e-aec4-9eda7335d164 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=735761e0-a79d-469e-aec4-9eda7335d164

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Jolicloud robby (PreFinal Release), kernel 2.6.32.9-1-jolicloud
uuid		735761e0-a79d-469e-aec4-9eda7335d164
kernel		/boot/vmlinuz-2.6.32.9-1-jolicloud root=UUID=735761e0-a79d-469e-aec4-9eda7335d164 ro quiet splash 
initrd		/boot/initrd.img-2.6.32.9-1-jolicloud
quiet

title		Jolicloud robby (PreFinal Release), kernel 2.6.32.9-1-jolicloud (recovery mode)
uuid		735761e0-a79d-469e-aec4-9eda7335d164
kernel		/boot/vmlinuz-2.6.32.9-1-jolicloud root=UUID=735761e0-a79d-469e-aec4-9eda7335d164 ro  single
initrd		/boot/initrd.img-2.6.32.9-1-jolicloud

title		Jolicloud robby (PreFinal Release), memtest86+
uuid		735761e0-a79d-469e-aec4-9eda7335d164
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
chainloader	+1

---

### Post by thahir1986 on 2010-07-21
Backup ur menu.lst and replace ur content with the below one. :p


```
# menu.lst - See: grub(:cool:, info grub, update-grub(:cool:
#            grub-install(:cool:, grub-floppy(:cool:,
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
timeout 30 

## debug [on | off | normal | status | INTEGER]
# Turn on/off or display/set the debug level.
debug		off

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
# kopt=root=UUID=735761e0-a79d-469e-aec4-9eda7335d164 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=735761e0-a79d-469e-aec4-9eda7335d164

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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
# This entry automatically added by the Debian installer for a non-linux OS
 # on /dev/sda1
 title		Windows Vista (loader)
 rootnoverify	(hd0,0)
 savedefault
 chainloader	+1


title		Jolicloud robby (PreFinal Release), kernel 2.6.32.9-1-jolicloud
uuid		735761e0-a79d-469e-aec4-9eda7335d164
kernel		/boot/vmlinuz-2.6.32.9-1-jolicloud root=UUID=735761e0-a79d-469e-aec4-9eda7335d164 ro quiet splash 
initrd		/boot/initrd.img-2.6.32.9-1-jolicloud
quiet

title		Jolicloud robby (PreFinal Release), kernel 2.6.32.9-1-jolicloud (recovery mode)
uuid		735761e0-a79d-469e-aec4-9eda7335d164
kernel		/boot/vmlinuz-2.6.32.9-1-jolicloud root=UUID=735761e0-a79d-469e-aec4-9eda7335d164 ro  single
initrd		/boot/initrd.img-2.6.32.9-1-jolicloud

title		Jolicloud robby (PreFinal Release), memtest86+
uuid		735761e0-a79d-469e-aec4-9eda7335d164
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


```

---

### Post by aliboy on 2010-07-21
just like to add, boot loader boots ubuntu 10.04 first but menu.lst is located in jolicloud partition. will there be no problem to replace those codes?

---

### Post by aliboy on 2010-07-21
just like to add, boot loader boots ubuntu 10.04 first but menu.lst is located in jolicloud partition. will there be no problem to replace those codes??

---

### Post by thahir1986 on 2010-07-21
i did not change any partition location....i was just change the timeout from 10 to 30 seconds and move this below code from the bottom to above the default one....

 title		Windows Vista (loader)
 rootnoverify	(hd0,0)
 savedefault
 chainloader	+1

that's all...i think what did u mean..or anything ?

---

### Post by aliboy on 2010-07-21
thats exactly what i want. thnaks!

i have another question. from the menu.lst ive shown, why is it that i cant see any description that it include ubuntu 10.04 in the bootlist? what is obvious for me is the list for jolicloud and windows OS.

---

### Post by thahir1986 on 2010-07-21
U  have jolicoud os not ubuntu 10.04 ...i didn't use that one...i think that different linux product link ubuntu , debian, etc...

---

### Post by aliboy on 2010-07-21
:D

i mean right now i have 3 OS installed in HD. if im going to boot the PC, it will show the the boot list first is ubuntu 10.04 then windows OS and last is jolicloud. the default OS is ubuntu 10.04. 

If i try to open menu.lst(using terminal) in ubuntu 10.04, it will open the file but its blank. (if i go browse the grub folder, there is no menu.lst listed)
If i try to boot on jolicloud and open the menu.lst, i will show the one I posted.

is this normal?

---

### Post by thahir1986 on 2010-07-21
omg!..i think the menu.lst  you was posted is not active now...so whatever the changes we made  that doesn't show in ur grub menu..because u installed the 10.04 as the 3rd OS. Ubuntu 10.04 have grub2 boot loader. I'm not have the ubuntu 10.04, so i don't know how to do this...check this [link]("http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/") , may be it will help u,

To know about the basics of the grub 2..read this [thread]("http://ubuntuforums.org/showthread.php?t=1195275")

Thanks .

---

