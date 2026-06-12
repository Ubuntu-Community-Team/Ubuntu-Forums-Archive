---
title: "Grub Error 17"
date: 2006-12-26
forum: Installation &amp; Upgrades
---

### Post by MERLIN2049ER on 2006-12-26
Hi, I've had ubuntu 6.10 installed on an external usb hard drive for awhile until I got Grub Error 17 when I boot up.

I've looked into the Grub Error 17 - basically it can't mount or find my linux partition.  
My Ubuntu 6.10 installation is on /dev/sdc1.  I ran a fisk -l , the other 2 partitions are my windows partitions.  

------------
fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
16 heads, 63 sectors/track, 310101 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      310097   156288856+   7  HPFS/NTFS

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       14031   112703976    7  HPFS/NTFS
/dev/sdc2           14032       14593     4514265    f  W95 Ext'd (LBA)
/dev/sdc5           14032       14593     4514233+  82  Linux swap / Solaris
----------------

Just wondering, it doesn't look normal.  lol.  I'm not too sure what /dev/sdc2 is,   /dev/sdc1 should be my first ubuntu partition. 

Where can I find some help repairing my installation.  I got some stuff on it , so as a last resort I don't want to reformat/ re-install.  

:-k 

Thanks in advance,
Joe.

---

### Post by dbbolton on 2006-12-27
with all of my grub problems, i've had to boot off a live cd and edit the configuration files from there. but, i've never encoutered error 17. sorry :(

hopefully someone who knows what theyre doing will come along soon

---

### Post by cotcot on 2006-12-27
There is obviously a problem with sdc1. 
I suggest to back-up sdc1 using tar or partimage. Put a new filesystem on sdc1 (sudo mke2fs -j /dev/sdc1 if you want it ext3) ; restore the backup. MAKE SURE SDC1 IS YOUR UBUNTU !
 
tar HOWTO : [http://www.debianhelp.co.uk/tarbackup.htm]("http://www.debianhelp.co.uk/tarbackup.htm")

---

### Post by MERLIN2049ER on 2006-12-27
ok , I figured out my own problem.  

I used Arconis Disk Director to change the partition type from NTFS to XT3 (or 82), the linux swap file is (83).

I rebooted into Ubuntu ok, it just had to run a disk check because it wasn't shutdown properly.

Thanks,
Joe.

---

### Post by liveforfunnow on 2006-12-29
can you explain that Acronis Disk Director part? i recently reinstalled Ubuntu, and cannot use GRUB. here is my setup:

All SATA2.

/dev/sda: 400 GB NTFS, just data no OS
/dev/sdb: 250 GB NTFS, winblowsXP installed
/dev/sdc: 250 GB EXT3, 6.06 installed

when i change the BIOS to boot from sdb, XP boots fine. when i switch it to sdc, grub comes up, but anything i choose (regular Ub, recovery UB, or X), grub gives error 17: "can't mount selected partition."

any ideas? thanks in advance!

---

### Post by cotcot on 2006-12-29
Check how grub sees you partitions.
You can chroot from the liveCD into your sdc and type grub.
Then (grub > is the prompt you see after typing grub) :

grub >  root=(hd         #press TAB after the d of hd and this will show you the disks that grub sees

Do the same for your sdc :

grub >  root=(hd2,         #press TAB after the d of hd and this will show you the partitions with their filesystem type on sdc as grub sees them.

Check if the filesystems are as you expect them (see /etc/fstab). Compare the root=(hd TAB output with the output from sudo fdisk -l.

I had it that grub saw the partitions but not the filesystems although the filesystems were OK according to sudo fdisk -l.

An alternative that worked by me (also on a usb hdd) was installing lilo.

---

### Post by liveforfunnow on 2006-12-29
i apologize, but that bit is not clear to me. I tend to be dense when it comes to the Terminal. here is a solution i tried (but did not work):

used a Hiren's BootCD to boot into Acronis Disk Director, and checked the filesystems. they were in order; EXT3 for sdc with a 3 GB swap. 

what can i change in the liveCD's Terminal to fix the error? i've reinstalled Kubuntu 6.10 and Ubuntu 6.06; neither fix the error. is there any way to wipe GRUB and start over (without destroying the MBR)?

thanks!

---

### Post by bulldog on 2006-12-29
Please report us the output of
```
sudo fdisk -l (l as in like)
```

I think your ubuntu entry points to the wrong disk.
To determine that,we have to boot the live cd and mount your ubuntu.
```
sudo mkdir /mnt/rescue
sudo mount /dev/sdc? /mnt/rescue  (you have to switch the ? with the partition number)
gksudo gedit /mnt/rescue/boot/grub/menu.lst
```

---

### Post by liveforfunnow on 2006-12-31
Ok, thanks for the help. I discovered that if I put in the 6.06 liveCD, but at the boot menu choose "boot from first hard disk," Grub comes up. Anything i choose from THAT menu loads fine. i was able to boot into 6.06, upgrade to 6.10, and install nvidia drivers. when i take out the livecd, however, the Grub that comes up still gives the error 17.

weird, huh?

here is my sudo fdisk -l:

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       48264   387680548+   7  HPFS/NTFS
/dev/sda2           48265       48641     3028252+   5  Extended
/dev/sda5           48265       48641     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       27666   222227113+   7  HPFS/NTFS
/dev/sdb2           27667       30401    21968887+   5  Extended
/dev/sdb5           27667       30401    21968856    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30023   241159716   83  Linux
/dev/sdc2           30024       30401     3036285    5  Extended
/dev/sdc5           30024       30401     3036253+  82  Linux swap / Solaris

Disk /dev/sdd: 2097 MB, 2097152000 bytes
255 heads, 63 sectors/track, 254 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         255     2047968+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(253, 254, 63) logical=(254, 245, 55)


thanks!

---

### Post by bulldog on 2006-12-31
> **liveforfunnow said:**
> Ok, thanks for the help. I discovered that if I put in the 6.06 liveCD, but at the boot menu choose "boot from first hard disk," Grub comes up. Anything i choose from THAT menu loads fine. i was able to boot into 6.06, upgrade to 6.10, and install nvidia drivers. when i take out the livecd, however, the Grub that comes up still gives the error 17.

weird, huh?

here is my sudo fdisk -l:

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       48264   387680548+   7  HPFS/NTFS
/dev/sda2           48265       48641     3028252+   5  Extended
/dev/sda5           48265       48641     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       27666   222227113+   7  HPFS/NTFS
/dev/sdb2           27667       30401    21968887+   5  Extended
/dev/sdb5           27667       30401    21968856    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30023   241159716   83  Linux
/dev/sdc2           30024       30401     3036285    5  Extended
/dev/sdc5           30024       30401     3036253+  82  Linux swap / Solaris

Disk /dev/sdd: 2097 MB, 2097152000 bytes
255 heads, 63 sectors/track, 254 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         255     2047968+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(253, 254, 63) logical=(254, 245, 55)


thanks!

This is nice,though I need the menu.lst as well to see what's wrong with it.
If you can boot into ubuntu,you can copy the menu.lst with to following command,
```
gksudo gedit /boot/grub/menu.lst
```
And to see the boot order as how GRUB will see it,maybe you can give me the output of
```
cat /boot/grub/device.map
```

---

### Post by liveforfunnow on 2007-01-01
here is the info you requested. remember, i am booted into Ubuntu after loading LiveCD 6.06 and choosing "Boot from first hard disk," and then the appropriate GRUB entry. when i boot normally, the same GRUB entry gives error 17.

MENU.LST:

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
# kopt=root=UUID=375ed02f-f257-47b7-9143-9778b36042df ro

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

title		Ubuntu, kernel 2.6.17-10-386
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=375ed02f-f257-47b7-9143-9778b36042df ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=375ed02f-f257-47b7-9143-9778b36042df ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=375ed02f-f257-47b7-9143-9778b36042df ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=375ed02f-f257-47b7-9143-9778b36042df ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=375ed02f-f257-47b7-9143-9778b36042df ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=375ed02f-f257-47b7-9143-9778b36042df ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=375ed02f-f257-47b7-9143-9778b36042df ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=375ed02f-f257-47b7-9143-9778b36042df ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

END MENU.LST

and...

(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc

thanks again!

---

### Post by bulldog on 2007-01-01
Make the sdc your default boot device,GRUB is installed in the MBR of this disk so you should use it to boot from.
It will be (hd0) instead of (hd2) so you have to modify all the entry's in your menu.lst to (hd0,0) instead of (hd2,0) as they are now.
```
MENU.LST:

# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=375ed02f-f257-47b7-9143-9778b36042df ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title Ubuntu, kernel 2.6.17-10-386
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-386 root=UUID=375ed02f-f257-47b7-9143-9778b36042df ro quiet splash
initrd /boot/initrd.img-2.6.17-10-386
savedefault
boot

title Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-386 root=UUID=375ed02f-f257-47b7-9143-9778b36042df ro single
initrd /boot/initrd.img-2.6.17-10-386
boot

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=UUID=375ed02f-f257-47b7-9143-9778b36042df ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=UUID=375ed02f-f257-47b7-9143-9778b36042df ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, kernel 2.6.15-27-386
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-27-386 root=UUID=375ed02f-f257-47b7-9143-9778b36042df ro quiet splash
initrd /boot/initrd.img-2.6.15-27-386
savedefault
boot

title Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-27-386 root=UUID=375ed02f-f257-47b7-9143-9778b36042df ro single
initrd /boot/initrd.img-2.6.15-27-386
boot

title Ubuntu, kernel 2.6.15-26-386
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-26-386 root=UUID=375ed02f-f257-47b7-9143-9778b36042df ro quiet splash
initrd /boot/initrd.img-2.6.15-26-386
savedefault
boot

title Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-26-386 root=UUID=375ed02f-f257-47b7-9143-9778b36042df ro single
initrd /boot/initrd.img-2.6.15-26-386
boot

title Ubuntu, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Home Edition
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

```

If you copy this menu.lst over your's it should work,however you have all the UUID's in your menu.lst,which I don't have.
Mine just point to sdc0 instead of the UUID,but give it a try.
The windows entry should work this way too,but it's possible if you make the sdc boot device your windows disk will become (hd2) so if this entry won't work we'll have to change that one,but give it a try first so we can see if there are any errors.

---

### Post by liveforfunnow on 2007-01-01
that worked perfectly! thanks so much!

any idea as to how this happened?

---

### Post by bulldog on 2007-01-01
Yes I have,that's why I could fix it :D

---

### Post by degsyw on 2007-03-12
because when your pc boots off the disk it becomes hd0 the primary disk in the machine from grubs perspective! when grub was installed it was to  the third disk in your machine (hd2) there are loads of these errors all over the forum, esp on external disks.

---

