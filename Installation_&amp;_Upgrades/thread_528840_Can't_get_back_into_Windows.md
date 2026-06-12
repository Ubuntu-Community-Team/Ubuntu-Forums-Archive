---
title: "Can't get back into Windows"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by Zeenomorph on 2007-08-18
I know that this has been done before, but i'm a complete noob, and don't know if I have any hope or not.  I'd be perfectly happy running only Linux, but after a month, I still can't get my on-board camera/mic to work, and they worked on XP, so that's what I thought that I'd go back to.

I bought this laptop new.  It's an Asus F5V.  I installed XP, everthing was good.  But I hate Windows (read: Microsoft) so I installed Linux, and there was much rejoicing.  

Windows was installed on my first partition, C:  Then I installed Ubuntu, I used the default method.  There is no Windows option through Grub.

I've seen people ask to see my menu.lst file so here it is;

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
# kopt=root=/dev/mapper/Mojo-root ro

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.20-16-generic root=/dev/mapper/Mojo-root ro quiet splash
initrd		/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.20-16-generic root=/dev/mapper/Mojo-root ro single
initrd		/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-generic root=/dev/mapper/Mojo-root ro quiet splash
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) 
root		(hd0,0) 
kernel		/vmlinuz-2.6.20-15-generic root=/dev/mapper/Mojo-root ro single 
initrd		/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

and the result of a fdisk;

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32        9729    77899185    5  Extended
/dev/sda5              32        9729    77899153+  8e  Linux LVM

Disk /dev/sdb: 256 MB, 256901120 bytes
16 heads, 32 sectors/track, 980 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         980      250864    6  FAT16


I think I lost Windows, is there anything that I can do?

---

### Post by Pumalite on 2007-08-18
Post sudo fdisk -l (small L)

---

### Post by Zeenomorph on 2007-08-18
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32        9729    77899185    5  Extended
/dev/sda5              32        9729    77899153+  8e  Linux LVM

Disk /dev/sdb: 256 MB, 256901120 bytes
16 heads, 32 sectors/track, 980 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         980      250864    6  FAT16

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9729    78148161    7  HPFS/NTFS

---

### Post by Pumalite on 2007-08-18
Backup your menu.lst:
cp /boot/grub/menu.lst /boot/grub/menu.lst.back
Edit your menu.lst:
gksudo gedit /boot/grub/menu.lst
Add the following to the end of your menu.lst (below memtest):

title Windows XP
root (hd2,0)
makeactive
chainloader +1

Reboot and let's see.

---

### Post by Zeenomorph on 2007-08-18
I did that.. went into Grub, and selected XP then;

Error 21:  Selected disk does not exist

---

### Post by Pumalite on 2007-08-18
According to your fdisk -l, you have XP in sdc1. Windblows likes and want to be sda. It might be necessary to set sdc as sda in your computer, then reinstall Grub with Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

This is for your info:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21)

---

### Post by Zeenomorph on 2007-08-18
I'm terribly sorry to inconvenience you further, but I have to admit that I have no idea what to do.  This is a problem for me, I've looked through forum postings, and observed many helpful people such as yourself giving advice, as you just did, and helping people through their problems.  It all looks so good until I actually have to comprehend what is being told to me.

I've never really done anything with my Windows computer besides point and click, I understand that all of this is probably rudimentary to you, but please have some empathy for someone who has no idea what those links you posted mean.  It might as well be Greek, or Chinese to me!

What is the next step?  What do I need to do?  Please use small words, I don't seem to be as technically gifted as yourself.

Thank you for your patience in this;

Zeenomorph

---

### Post by Pumalite on 2007-08-18
Let's try one more thing: edit your menu.lst; in the XP entry change 'root' for 'rootnoverify' Reboot and let's see what happens.

---

### Post by Zeenomorph on 2007-08-18
Did that.  Same thing.  Disk does not exist.

---

### Post by Pumalite on 2007-08-18
Post 'cat /etc/fstab' and 'blkid'

---

### Post by Zeenomorph on 2007-08-18
mojo@Mojo:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Mojo-root /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=198aa209-cb20-42eb-9e2b-cde9f455b3eb /boot           ext3    defaults        0       2
/dev/mapper/Mojo-swap_1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


mojo@Mojo:~$ blkid
/dev/mapper/Mojo-root: UUID="451e548b-c5fb-48a5-be60-3facb4dbb040" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/Mojo-swap_1: UUID="59f30226-8686-4f08-876c-98ea7c3bd61b" TYPE="swap" 
/dev/sda1: UUID="198aa209-cb20-42eb-9e2b-cde9f455b3eb" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: SEC_TYPE="msdos" UUID="46BB-0706" TYPE="vfat"

---

### Post by Pumalite on 2007-08-18
Well .I'm lost. How many drives do you have? Was XP installed first? I don't see it anywhere. But, according to your fdisk -l, you have an sdc formatted ntfs. This is not reflected in your fstab nor blkid??? We could have edited fstab with the contents of 'blkid', but I don't see it. Therefore the questions.

---

### Post by Zeenomorph on 2007-08-18
I installed XP with a C: and a D:  My harddrive is 80gb so I made D: into D and E.  then I put Linux on the empty drive E: ...... i think...... do you think that I somehow overwrote my XP?

---

### Post by Pumalite on 2007-08-18
Before you start fresh: stick your XP CD, hit 'r' for Recovery Console, then: FIXMBR>FIXBOOT. If you have a Windows system, that will bring it back. Later we can worry about re-installing Grub. Try it.

---

### Post by Zeenomorph on 2007-08-18
I would love to do as you've recommended.   I can't seem to be able to find my Windows disk at the moment.  I'll post when I can, I don't expect it to be soon, it might be at my other house.... =+(

---

### Post by Pumalite on 2007-08-18
Good luck!

---

### Post by Zeenomorph on 2007-08-18
Lucky me, I found the disk!  I'm trying what you said now.

---

### Post by Zeenomorph on 2007-08-18
I think my system is really buggered up.  I put in my XP disk, and booted from it.  The screen went black.  Nothing.  No curser.  No flashing white block, nothing.  It stayed black for 5 minutes, and the whole time the computer was quiet, It didn't sound like anything was going on.  I did a hard reboot, and got back into Linux.

I imagine that my dreams of a dual boot system are fading into darkness..... =+(

---

### Post by merlinus on 2007-08-18
Perhaps your computer is trying to tell you something about the futility of trying to coexist with Gatesville?

:)

-merlin

---

### Post by Pumalite on 2007-08-18
Not yet. Go into your BIOS and make sure that CD-DVD is first in the boot order.

---

### Post by Zeenomorph on 2007-08-18
Sorry for the delay in posting this, I had to pick up the wife from work.

re Merlinus:  I agree, I hate that I'm even attempting this, but I just can't get my camera/mic working on Linux.  And they both worked fine on XP.  I assure you that I want nothing to do with Mr. Gates on my machine.

The bios is set to CD as the primary boot device.

---

### Post by Zeenomorph on 2007-08-19
/bump

It's probably bad form to bump my own thread, but I'm hoping that someone can either give me advice or tell me that it's hopeless.

If it is hopeless I can deal with it.  I don't really want Windows anyway, it's the wife who wants the camera/mic to work, I don't really care.

That said, I'd still like to know one way or the other.

---

### Post by Pumalite on 2007-08-19
What do you wait then?! Use Gparted : [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
Make one large partition and install.

---

### Post by Zeenomorph on 2007-08-19
I don't understand?  How does that work?  What am I to do?

---

### Post by Pumalite on 2007-08-19
Did you make the bootable CD of Gparted? Read the Documentation. Gparted boots, it has a graphical interface, you click on all the partitions you have and delete them; then click again>Go to>Partitions>New>Make one whole partition of the entire disk>Format Ext3 if you want (not necessary). Install>Guided-Use entire Disk. Or, if Alternate CD; follow the instructions. Google Ubuntu alternate CD Installation.

---

