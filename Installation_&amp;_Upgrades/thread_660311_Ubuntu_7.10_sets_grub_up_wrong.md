---
title: "Ubuntu 7.10 sets grub up wrong"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by jej2003 on 2008-01-06
The last time I installed ubuntu from an Xubuntu cd grub detected my drives fine, no problem at all, this time, when I installed from a minimal cd grub detected my drives differently, and wrong.  For whatever reason in grub it says my linux root is (hd2,0) when it is (hd1,0) and my windows partition is hd0,0 but it says it is hd1,0, it is easy enough to fix, but everytime i upgrade the kernel I have to fix this.  How can I fix this for good?

---

### Post by logos34 on 2008-01-06
Post your menu.lst.  it could be the 'groot' line

---

### Post by jej2003 on 2008-01-07
Yeah I see groot listed as hd2,0, from what I have read this should be the bootable partition correct?  My bootable linux partition is actually hd1,0.  I have updated it, but I think the install screws up my Windows entry as well.....will have to check when next kernel is released.

Is there a way to force the installers to update this file, by either reinstalling grub, kernel, etc?
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
# kopt=root=UUID=b4b3f951-c121-478d-8289-d98e28370620 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=b4b3f951-c121-478d-8289-d98e28370620 ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=b4b3f951-c121-478d-8289-d98e28370620 ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, memtest86+
root        (hd2,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1


```

---

### Post by logos34 on 2008-01-07
can you also post 

sudo fdisk -l

---

### Post by jej2003 on 2008-01-09
```
 sudo fdisk -l


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x49e049df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   c  W95 FAT32 (LBA)
/dev/sda2            3825        9728    47423880    f  W95 Ext'd (LBA)
/dev/sda5            3825        9728    47423848+   7  HPFS/NTFS

Disk /dev/sdb: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a894a88

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2382    19133383+  83  Linux
/dev/sdb2            2383        2491      875542+   5  Extended
/dev/sdb5            2383        2491      875511   82  Linux swap / Solaris

Disk /dev/sdc: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ebab43f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       20023   160834716    7  HPFS/NTFS

```

---

### Post by logos34 on 2008-01-10
This is a hard one:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Home Edition
root        (hd0,0)

doesn't match

>    Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       20023   160834716    7  HPFS/NTFS

Sorry, I can't make sense out of this without more info.  Are these mixed sata and ide drives? 
Maybe there's an issue involving the storage controller(s) and your Bios not recognizing the drives consistently.  

If your only problem is after a kernel update, then it might be easier to just manually change menu.lst back each time before you reboot.  

Maybe someone else has a suggestion that won't cause you bigger problems in the process (like not being able to boot at all!).

---

### Post by tact on 2008-01-10
Not sure if this has any bearing on your problem but maybe it will help....

I routinely clone the HDD inside my laptop to an external drive.  I use dd from the commandline.  It results in a complete clone of the internal drive, right down to the UUID numbers of each partition.

This causes only one minor issue for me, later when I plug the external drive in to do incremental backups with grsync... because the UUIDs of partitions on the internal and external drive are the same the system cannot "auto mount" the external drive partitions and I have to do that manually.

I found out I can change the UUIDs on the cloned drive and that solves the minor issue.  

Thanks for your patience - here is where it may be helpful to you:

When I change the UUID's on the cloned drive (and this also happens for you when you format a drive - you mentioned reinstalling - did you format partitions?) - I have to change the lines in /etc/fstab and /boot/grub/menu.lst to match.

If I change the grub menu.lst manually (edit using gedit etc..) at any time later if the update-grub command is launched (as happens when there is a kernel upgrade) somehow the OLD drive UUIDs are put back into the grub menu and I would have to manually edit again.

I have no idea wherer and how the system finds the old partition UUIDs but it does.  Good news is that this can be fixed.

To get "update-grub" to wake up and capture the new UUIDs and thus not have old settings restored every time there is a new kernel update you must:
1.  manually edit and get your system booted into ubuntu
2.  delete (or move/rename) the existing /boot/grub/menu.lst file.  deleting it is fine and safe.  it gets recreated.
3.  now pull up a terminal and run "sudo update-grub".

This should now force grub to re-look at all your partitions... automatically update its list of what partition has what UUID...  automatically create a shiny new and correct menu.lst ... and any future runs of update-grub picks up the correct info.  no more need to manually edit menu.lst after any kernel update.

Helped?

---

