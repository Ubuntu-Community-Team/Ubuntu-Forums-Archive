---
title: "Grub &amp; Unknown characters"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by PROCYYON on 2008-01-08
Ive installed XP on a WD hard disk and Kubuntu on a Seagate Hard disk. (Windows 1st)

The installation was successfully with no errors but when ive restart my pc ive come to this screen


[[IMG]http://img513.imageshack.us/img513/8426/kubjv7.th.jpg[/IMG]](http://img513.imageshack.us/my.php?image=kubjv7.jpg)

---

### Post by Pumalite on 2008-01-08
Strange indeed. Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by PROCYYON on 2008-01-12
sorry for my delay.

What do you want for me to do?

I cant boot on Kubuntu.

Ive installed ubuntu with the same problem.

---

### Post by Pumalite on 2008-01-12
Can you boot a Live CD?

---

### Post by PROCYYON on 2008-01-13
Yes. And I can see the hdd with ubuntu files inside from the live cd

Maybe is problem with hdd's MBR. Can i write grub into partition with XP?

---

### Post by Pumalite on 2008-01-13
Then post the output of the commands I gave you from the Live CD Terminal.

---

### Post by PROCYYON on 2008-01-13
From fdisk ive got

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb2244c5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488392064   244196001    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    74862899    37431418+  83  Linux
/dev/sdb2        74862900    78156224     1646662+   5  Extended
/dev/sdb5        74862963    78156224     1646631   82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x03260326

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   249762554   124881246    7  HPFS/NTFS
/dev/sdc2       249762555   488392064   119314755    f  W95 Ext'd (LBA)
/dev/sdc5       249762618   488392064   119314723+   7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x64fbd418

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   976768064   488384001   42  SFS
ubuntu@ubuntu:~$ 







From cat ive got "No such file or director" so i had to go manually to menu.lst

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
# kopt=root=UUID=2d87b6d3-c40f-40ff-8de2-35811a4cbc48 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2d87b6d3-c40f-40ff-8de2-35811a4cbc48 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2d87b6d3-c40f-40ff-8de2-35811a4cbc48 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

---

### Post by Pumalite on 2008-01-13
Were all the hard drives connected when you installed? I assume your Ubuntu is in sdb1, but Windows is in sdc1, so the question is: Didi you install Windows after Ubuntu? Your 500 GB drive is empty maybe not formatted.

---

### Post by PROCYYON on 2008-01-13
Ive installed 1st XP on WD 250GB sata II and ubuntu into 40GB IDE seagate.

WD 250GB IDE & 500GB  sata II seagate is for Storage (both using in XP)

The weird is that i can see the 40GB (ext3)  from my xp but of course i cant access it.

---

### Post by Pumalite on 2008-01-13
Maybe this can help you:
[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)

---

### Post by Pumalite on 2008-01-13
Also, you might want to try reinstalling Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by PROCYYON on 2008-01-13
Ive decided to install Ubuntu in the 40GB HDD but im going to install grub into partition with windows Boot loader


Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x03260326

Device Boot Start End Blocks Id System
/dev/sdc1 * 63 249762554 124881246 7 HPFS/NTFS
/dev/sdc2 249762555 488392064 119314755 f W95 Ext'd (LBA)
/dev/sdc5 249762618 488392064 119314723+ 7 HPFS/NTFS



So that HDD is Sata II. how i can determine the hd ?,?.... is hd0,0?

---

### Post by Pumalite on 2008-01-13
Your 40 GB SATA HDD does not show up in your fdisk -lu???

---

### Post by PROCYYON on 2008-01-13
It shows but i have installed Ubuntu over 7 times in this hdd now and i get the same screen. (The 40GB hdd is pATA)

Maybe its fault of hdd's MBR. So i want to installed grub into windows partitions.

---

### Post by Pumalite on 2008-01-13
It's your best choice.
Show me the whole output, so I can help you identify it.

---

### Post by PROCYYON on 2008-01-13
you mean that?

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb2244c5e

Device Boot Start End Blocks Id System
/dev/sda1 * 63 488392064 244196001 7 HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Device Boot Start End Blocks Id System
/dev/sdb1 * 63 74862899 37431418+ 83 Linux
/dev/sdb2 74862900 78156224 1646662+ 5 Extended
/dev/sdb5 74862963 78156224 1646631 82 Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x03260326

Device Boot Start End Blocks Id System
/dev/sdc1 * 63 249762554 124881246 7 HPFS/NTFS
/dev/sdc2 249762555 488392064 119314755 f W95 Ext'd (LBA)
/dev/sdc5 249762618 488392064 119314723+ 7 HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x64fbd418

Device Boot Start End Blocks Id System
/dev/sdd1 63 976768064 488384001 42 SFS
ubuntu@ubuntu:~$

---

### Post by Pumalite on 2008-01-13
Your 40 GB HDD is sdb; it looks like you have a system installed already there. You have 3 boot flags, which is fine if you want to boot each system changing the boot order in BIOS. I would use Gparted to remove the boot flags except sda1, then try to reinstall Grub to sda. You might save yourself a reinstall.

---

### Post by PROCYYON on 2008-01-15
finally ive installed ubuntu in the same disk as Windows and everything runs perfect,
So something is going on with the 40GB disk!!!

THX for your time

---

### Post by Pumalite on 2008-01-15
When you have a mix of IDE and SATA is better to install both OS's in one drive and keep the other for storage.

---

