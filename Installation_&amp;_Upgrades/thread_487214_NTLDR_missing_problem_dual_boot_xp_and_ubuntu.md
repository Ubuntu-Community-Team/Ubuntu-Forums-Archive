---
title: "NTLDR missing problem dual boot xp and ubuntu"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by t1234 on 2007-06-28
Hi
I have searched on the net and read some solutions in forums but cannot fix my problem. I am hoping I have missed the obvious and another pair of eyes will spot it ..... I will try and explain everything as I did it.

I was running windows xp on 80gb sata drive with data disk on 160gb ide channel. BIOS boot order was xp 80gb as first hard drive after the cd-rom drive. I realised I had a spare 80gb drive (ide) so decided to install Ubuntu. I disconnected the 80gb xp drive and the 160gb drive whilst installing Ubuntu on the 80gb ide as master. Install was fine, everything works fine, detected all hardware with no problems - very impressed. 
Next I reconnected the drives, 80gb xp drive going back as primary sata and 160gb data as secondary ide with the Ubuntu 80 gb remaining as master. BIOS boot order now Ubuntu first and xp 2nd. 

I edited /boot/grub/device.map and /boot/grub/menu.lst as per various threads to have the option of booting either xp or Ubuntu through grub. Ubuntu boots fine from grub, xp returns the error NTLDR is missing. If I reset the BIOS boot order to boot straight to xp disk then xp boots fine. As I need the xp for work I am very reluctant to change anything on this setup. I can currently boot into either disk using the BIOS but would like to get grub working as it is looks much cleaner. 

I'd be grateful for any suggestions ..... here is menu.lst, device.map, fdisk -l.

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
timeout         8

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

  
title              Windows XP Home 
root               (hd2,0)
map                (hd0) (hd2)
map                (hd2) (hd0)
savedefault
makeactive
chainloader        +1


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
# kopt=root=UUID=c26c3f44-9f28-4c8f-9bb5-38aa20073305 ro

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=c26c3f44-9f28-4c8f-9bb5-38aa20073305 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=c26c3f44-9f28-4c8f-9bb5-38aa20073305 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=c26c3f44-9f28-4c8f-9bb5-38aa20073305 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=c26c3f44-9f28-4c8f-9bb5-38aa20073305 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

###device.map

(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc


### fdisk -l

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9590    77031643+  83  Linux
/dev/sda2            9591        9964     3004155    5  Extended
/dev/sda5            9591        9964     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       20023   160834716    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9728    78140128+   7  HPFS/NTFS

---

### Post by Pumalite on 2007-06-28
Leave the set up with XP 1st, Ubuntu 2nr. Then reinstall Grub with Super Grub; it will have a menu with XP and Ubuntu.

[http://users.bigpond.net.au/hermanzone/p15.htm#How_To_boot_Windows_using_GRUBs_CLI](http://users.bigpond.net.au/hermanzone/p15.htm#How_To_boot_Windows_using_GRUBs_CLI)

Take a look at this too:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by confused57 on 2007-06-28
You might want to try this Window's entry:
```
title Windows XP Home
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1
```

---

### Post by t1234 on 2007-06-29
I changed the device.map to 

(hd0)   /dev/sda
(hd1)   /dev/sdc
(hd2)   /dev/sdb

then followed the entry as per confused57 post and now its all working fine. I can boot into either Ubuntu or xp without changing anything on my xp install.

Thanks a lot for your help !

---

### Post by Lamez on 2007-06-29
You need to fix your master boot record a.k.a MBR

---

### Post by t1234 on 2007-06-30
I haven't had to alter my MBR, following confused57 post it is all working fine.

The machine will boot using grub into either xp or ubuntu with no changes whatsoever to the windows xp set up. Grub is on the ubuntu disk. I have even tested changing the BIOS order to boot first into xp and that works too. 

Its great that there is a method of installing ubuntu that does not interfere with the current xp installation for those who need it for work and don't want to risk damaging it.

---

