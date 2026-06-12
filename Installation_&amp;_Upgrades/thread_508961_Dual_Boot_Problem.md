---
title: "Dual Boot Problem"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by cptInsane0 on 2007-07-24
Ok, I have a system with 2 160gig sata2 drives raided for my windows drive.  Also, there is a 120gb IDE and a 200GB IDE.  I installed Ubuntu on the 120gig.  It is partitioned as follows:

10gb: /
4GB: swap
25GB: Shared
Remainder: storage

I installed ubuntu onto the ten gig partition obviously.  Also, I told the boot loader to go to (hd0), which is the same drive as /dev/hda1, which is the 10 gig partition.  In my file browser, there is a /boot folder that contains a /grub folder.  the device.map file says hd0 is hda, so that shouldnt be a problem.  I need to create the ubuntu.bin file that i linked the boot.ini file in windows to create the menu.  The problem is, I can get the file to create in the shared drive like I want, but it keeps showing up as empty

I used dd if=/dev/hda1 of=/mnt/shared/ubuntu.bin bs=512 count=1

when I originally installed ubuntu, i told it to put the boot loader at dev/hda1.  When I created the .bin file, it had stuff in it.  I went to boot ubuntu from the NTloader, and it just came to a screen that said GRUB, and sat there.

I talked to a coworker, and he said grub doesnt see the drives as letters, it sees hd0,hd1, etc.  So I installed it again to hd0, and like I said, theres a directory for grub and everything.  I can't get it to work.  What should I do?

---

### Post by Pumalite on 2007-07-24
Post: 'sudo fdisk -l ( small L) and 'cat /etc/fstab' and 'cat /boot/grub/menu.lst'  BTW, 4GB of swap is waste of space; 1 GB is more than enough.

---

### Post by cptInsane0 on 2007-07-24
> **Pumalite said:**
> Post: 'sudo fdisk -l ( small L) and 'cat /etc/fstab' and 'cat /boot/grub/menu.lst'  BTW, 4GB of swap is waste of space; 1 GB is more than enough.

Ok, I have no problem repartitioning swap, I just heard you are supposed to put twice your ram as the swap file.  Is that all one command? Also, what will said command do?  I am obviously new to linux.

---

### Post by Pumalite on 2007-07-24
Each is a separate command. Take a look and you will know.

---

### Post by cptInsane0 on 2007-07-24
Ah, its a list.

ok, heres the fdisk info:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1216     9767488+  83  Linux
/dev/hda2            1217        4652    27599670    5  Extended
/dev/hda3            4653       14593    79851082+   7  HPFS/NTFS
/dev/hda5            1217        1714     4000153+  82  Linux swap / Solaris
/dev/hda6            1715        4652    23599453+   b  W95 FAT32

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       24792   199141708+   7  HPFS/NTFS

**Here's Menu.lst**
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
# kopt=root=UUID=0f9f7c1e-c755-48c5-bd1b-19fc6545125b ro

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0f9f7c1e-c755-48c5-bd1b-19fc6545125b ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0f9f7c1e-c755-48c5-bd1b-19fc6545125b ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

**Here's fstab**

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=0f9f7c1e-c755-48c5-bd1b-19fc6545125b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=98A0FCC3A0FCA940 /media/hda3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=5A34F5D534F5B45B /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=0BFD-40C0  /shared         vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=8943e3af-26ff-4b70-8c37-f3cfc6936f66 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0




Hopefully that will shed some light on things.  The sunglass guys are obviously 8's with parenthesis around them.

---

### Post by Pumalite on 2007-07-24
Get Gparted and fix sdb or at least see what's going on there. What are you supposed to have there?

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by cptInsane0 on 2007-07-24
sda and sdb are actually a raid array.  I use them for my windows drive.

---

### Post by Pumalite on 2007-07-24
Maybe that's your problem. Reading this "might" help: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by cptInsane0 on 2007-07-24
I appreciate the help, but that's not the situation.  I installed linux on a separate drive for that very reason.  I would think the thing to solve it would just be a way to point to the boot loader correctly.  Obviously I'm not creating the .bin file the right way if it shows up empty.  Since I plan on using the NT loader to boot ubuntu, all it would need to do is point to the right location on the hdd running linux.  Once again, thank you for all your help though.

---

### Post by Pumalite on 2007-07-24
Cant help you there. Don't know anything about windblows ( don't want to know )

---

### Post by confused57 on 2007-07-24
IMHO it would be easier to boot Windows from grub...something like the entry in this thread might work:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

I've never used boot.ini to boot Linux, so I can't help you there either.   There are several threads in the forum discussing this, though.

You could enter this command to see how grub recognizes the order of your hard drives:
```
gedit /boot/grub/device.map
```

---

### Post by cptInsane0 on 2007-07-24
That's ok, I still appreciate all the help.  I know there has to be a way to capture the booting information in a .bin file.  That's what everyone else trying my method is doing.  If I can get the file with the right information, I know how to point the NTbootloader to it

---

### Post by confused57 on 2007-07-24
> **cptInsane0 said:**
> That's ok, I still appreciate all the help.  I know there has to be a way to capture the booting information in a .bin file.  That's what everyone else trying my method is doing.  If I can get the file with the right information, I know how to point the NTbootloader to it
I may be wrong, but I believe I remember reading that grub's IPL needs to be installed on the root partition, in order to boot Ubuntu from boot.ini.

You might want to read over a few of the howto's & see if that is indeed the case...if it is, you can reinstall grub, using the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by cptInsane0 on 2007-07-24
hmmm, that link you posted mentioned loading grub to a partition too.  I bet what happened is when i chose (hd0), it put it in the mbr of that drive, when I should have said (hd0,0) to put it in the first partition

---

