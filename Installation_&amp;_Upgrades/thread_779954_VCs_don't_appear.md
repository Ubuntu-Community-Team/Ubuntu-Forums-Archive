---
title: "VCs don't appear"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by white_eagle-mk on 2008-05-03
I upgraded to Hardy before 3 days, and now I'm noticing that opening a Virtual Console (Ctrl-Alt-F[1-6]) doesn't work (and it worked perfectly in gutsy), the computer just stays in X

I have an ATi xpress 200m graphics card using the AiGLX method, eg the drivers from [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html) , because the drivers which ubuntu offered me don't have direct acceleration, nor hibernation and worked perfectly in Gutsy.

---

### Post by ddrichardson on 2008-05-04
What happens with CTRL-ALT-F8 and CTRL-ALT-F7 to switch out of GUI?

---

### Post by white_eagle-mk on 2008-05-04
> **ddrichardson said:**
> What happens with CTRL-ALT-F8 and CTRL-ALT-F7 to switch out of GUI?
Nothing happens,the computer stays in the GUI and also here is my menu.lst file ```
v# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=18d85731-f617-41ec-ac71-6e34fb34112f ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=18d85731-f617-41ec-ac71-6e34fb34112f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=18d85731-f617-41ec-ac71-6e34fb34112f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=18d85731-f617-41ec-ac71-6e34fb34112f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=18d85731-f617-41ec-ac71-6e34fb34112f ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I really need the VCs, if you could, please do help.

---

### Post by ddrichardson on 2008-05-04
Nothing happens at all?

From a terminal, what is the output of: ps aux|grep tty?

---

### Post by white_eagle-mk on 2008-05-05
> **ddrichardson said:**
> Nothing happens at all?

From a terminal, what is the output of: ps aux|grep tty?

The terminal window gives me this output:

```
whiteeagle@whiteeagle-laptop:~$ ps aux|grep tty
root      4211  0.0  0.1   1716   508 tty4     Ss+  14:08   0:00 /sbin/getty 38400 tty4
root      4212  0.0  0.1   1716   512 tty5     Ss+  14:08   0:00 /sbin/getty 38400 tty5
root      4216  0.0  0.1   1716   508 tty2     Ss+  14:08   0:00 /sbin/getty 38400 tty2
root      4217  0.0  0.1   1716   508 tty3     Ss+  14:08   0:00 /sbin/getty 38400 tty3
root      4219  0.0  0.1   1716   508 tty6     Ss+  14:08   0:00 /sbin/getty 38400 tty6
root      5555  4.3 13.7  76108 61792 tty7     Ss+  14:08   0:56 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root      5895  0.0 13.7  76108 61792 tty7     S+   14:08   0:00 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root      5928  0.0  0.1   1716   508 tty1     Ss+  14:08   0:00 /sbin/getty 38400 tty1
1000      6755  0.0  0.1   3008   772 pts/1    S+   14:30   0:00 grep tty
```

---

### Post by ddrichardson on 2008-05-05
OK so the tty are there the ATI module just isn't allowing access to them. I suspect you are experiencing something along the lines of Bug #129910, try the work around:

$ sudo sh -c "echo 'fbcon' >>/etc/initramfs-tools/modules"
 $ sudo update-initramfs -u

---

### Post by white_eagle-mk on 2008-05-05
Sorry, but I did what you told me and I rebooted after that, and ttys still don't show up, they just don't show up, X just stays in GUI mode.. :(
I should also mention that when I do a ctrl-alt-backspace (log off) the tty1 terminal shows up for a short time (i tried typing in it, it accepts it, and I can clearly see how everything went when I booted -- I have usplash removed it slows down my boot time for 3 mins), and then the computer goes to the login screen and I login and it still doesn't work after that...

---

### Post by white_eagle-mk on 2008-05-05
Also, I don't know why I have 2 kernels installed on my system and how they got there and how can I remove the older one. (I never tried clicking esc when GRUB boots up and login to the 2nd kernel).

---

### Post by ddrichardson on 2008-05-05
There are two kernel entries relates to Gutsy most likely..

That aside, this problem is most likely related to upgrading. I take it with a LiveCD session you have access to other virtual terminals?

I'd be inclined to disable the ATI driver, check to see if the problem is persistent, if not reinstall the ATI driver under Hardy.

I'd also consider opening your own bug with this as it is significantly different to the other bugs.

---

