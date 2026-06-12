---
title: "GRUB failing/nVidia X server not working?"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by JamesHarrison on 2007-06-11
Hi.

I'm running on a fairly modern machine- Intel Core 2, BFGTech nVidia 8800GTS graphics card and two gigs of RAM. I'm running Ubuntu 7.04 on a 80GB SATA drive, and have Windows XP (Ugh) on a 250GB SATA drive. 

The install went just fine, but after that it all got a bit pear shaped. 

I rebooted, let my BIOS boot off the WinXP drive to see if that worked- lo and behold, grub error 21. Booted to the Ubuntu disk, error 15. Googled error 15 on another machine, worked it out, LiveCD'd back in and had a look at the problem from there. Managed to get into Ubuntu by editing /mnt/myubuntudisk/boot/grub/menu.lst, swapping out
```
root (hd2,0)
```
For
```
root (hd0,0)
```

Now- Ubuntu sees my XP disk as /dev/sda1. But I can't get back into XP. I've tried all the roots in grub (0/1) and none boot- one gives a boot device error (0).

```

james@james-desktop:~$ sudo ls /dev | grep sd
sda
sda1
sdb
sdc
sdc1
sdc2
sdc5

```
Don't quite know where it's getting /dev/sdb from but it might be my DVD writer which is SATA.


Anyhow, got in to be greeted by an X failure message- turns out my nvidia drivers were refusing to load, saying the module could not be started (Should have written down the message but that was the gist of it). So I uninstalled the drivers (sudo apt-get remove nvidia-glx) and tried reinstalling to no avail. So I lynx'd to nVidia's website to download their drivers, grabbed the latest and went through the installer.

Everything works fine once it's running and I'm typing this on my Beryl'd up environment. However- every reboot, I have to reinstall drivers, or X fails with an incompatible kernel module error.

So- any clue on how I can get back into WinXP, and any ideas on this nvidia business?

---

### Post by logos34 on 2007-06-11
It appears you have the bios set to boot to grub on the mbr of 80gb ubuntu, which is why it works with '(hd0)'...That means windows may need  to be changed to (hd1)/sda2 both in the menu.lst AND the device.map file (also need to add 'map' lines to win entry in grub.

not sure about the nvidia problem.  

Please post your menu.lst, fstab and device.map

---

### Post by JamesHarrison on 2007-06-11
```

james@james-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=239c74ec-394c-491d-9f74-edb8a9cd6d31 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdc5
UUID=bc1304be-3598-4d28-bb05-60dcf1e93d63 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
james@james-desktop:~$ cat /boot/grub/menu.lst
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
color cyan/blue white/blue

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
# kopt=root=UUID=239c74ec-394c-491d-9f74-edb8a9cd6d31 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
groot=(hd0,0)

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
title           Ubuntu, kernel 2.6.20-16-generic (root 0,0
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=239c74ec-394c-491d-9f74-edb8a9cd6d31 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode) (root 0,0)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=239c74ec-394c-491d-9f74-edb8a9cd6d31 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=239c74ec-394c-491d-9f74-edb8a9cd6d31 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=239c74ec-394c-491d-9f74-edb8a9cd6d31 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=239c74ec-394c-491d-9f74-edb8a9cd6d31 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=239c74ec-394c-491d-9f74-edb8a9cd6d31 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd2,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition (root 0,0)
root            (hd0,0)
savedefault
makeactive
chainloader     +1
title           Microsoft Windows XP Home Edition (root 1,0)
root            (hd1,0)
savedefault
makeactive
chainloader     +1
title           Microsoft Windows XP Home Edition (root 2,0)
root            (hd2,0)
savedefault
makeactive
chainloader     +1

james@james-desktop:~$ cat /boot/grub/device.map
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc

```

---

### Post by logos34 on 2007-06-11
try this:

Ubuntu works, so backup grub config files and fstab just to be safe:
> [B]sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_bak
sudo cp /boot/grub/device.map /boot/grub/device.map_bak[/B]
sudo cp /etc/fstab /etc/fstab_bak

Then you need to swap the drive designations in device.map and add map lines to windows:

device.map:
> (hd**2**)   /dev/sda
(hd1)   /dev/sdb
(hd**0**)   /dev/sdc

menu.lst:

> ............

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition (root 2,0)
root            (hd**2**,0)
[B]map            (hd2) (hd0)
map            (hd0) (hd2)[/B]
savedefault
makeactive
chainloader     +1

then add a windows entry in fstab:
> 
**/dev/sda1 /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1**

there reason for the map lines is you need to fool windows into thinking it's frist in the bios hard disk boot order

give a shot  hope there's no typos

---

### Post by logos34 on 2007-06-11
knew I forgot something: (sorry!)

create the mount point for the windows:

**sudo mkdir /media/sda1**

---

### Post by JamesHarrison on 2007-06-12
Getting a grub error 21 on that- drive not found. Could it be grub is not seeing the CD drive and thinking in terms of 0,1 (sda,sdc) and not 0,1,2 (a,b,c)?

---

### Post by logos34 on 2007-06-12
> **JamesHarrison said:**
> Getting a grub error 21 on that- drive not found. Could it be grub is not seeing the CD drive and thinking in terms of 0,1 (sda,sdc) and not 0,1,2 (a,b,c)?

That sata dvd drive really muddied the waters...the thing is it shows up on device.map and the linux drive is designated '(hd2)'...maybe grub is indeed thinking in terms of hd0 hd1 / sda sdc ...substitute 'hd1' for hd2 in my suggestions above...maybe you've tried that by now

---

