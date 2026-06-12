---
title: "[SOLVED] GRUB problem?"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by solaceinsilence9 on 2008-03-26
Ok well, I installed Ubuntu got that going and working smoothly. So i loaded Partition Manager from the liveCD to resize and move my Partitions because I had a BIG gap of empty space between my DELL utility partition and my Vista partition. So after I defraged my Vista partition I went ahead and resize that partition as well as my Ubuntu partition and moved them closer to the front of my hard disk so combine all the free space. 

After that finished I booted Ubuntu. Runs and works like a dream. Vista is a different story. The GRUB menu comes up fine, but when I select Vista to load, it reboots my BIOS and drops me  back into the GRUB menu. I know my Vista partition is there and all the data is intack. So whats the problem? I found a similar post here:

[http://ubuntuforums.org/showthread.php?t=518814](http://ubuntuforums.org/showthread.php?t=518814)

So do I need to reinstall my GRUB menu? If so how exactly do I do that? Thanks for the help in advance. Its really kinda annoying. I FINALLY got Windows configured the way I wanted last night and got all my partitions size and moved the way I wanted but now I cant even load Windows. :confused:

---

### Post by kenpogi on 2008-03-26
hi, as a new user of ubuntu I cant offer much technical help, however have a look at this site and Google "supergrub".
It worked for me!!
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
The move to Linux has proved worthwhile despite the niggles!!

---

### Post by Rocket2DMn on 2008-03-26
From within Ubuntu can you post the output of these commands:
```
cat /boot/grub/menu.lst
sudo fdisk -l
cat /etc/fstab
```
This is so we can edit the grub list without reinstalling.  Otherwise the super grub disk should get you going by reinstalling GRUB.

---

### Post by Pumalite on 2008-03-26
I hope you initially allocated space for Ubuntu from WITHIN Vista.

---

### Post by solaceinsilence9 on 2008-03-26
Thanks, I will try supergrub if I cant get it fixed otherwise.

Here is the code.

benjamin@benjamin-laptop:~$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# kopt=root=UUID=19293c52-7cce-459c-bf40-050976a14ffa ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=19293c52-7cce-459c-bf40-050976a14ffa ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=19293c52-7cce-459c-bf40-050976a14ffa ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista/Longhorn (loader)
root            (hd0,1)
savedefault
makeactive
chainloader     +1

benjamin@benjamin-laptop:~$ sudo fdisk -l
[sudo] password for benjamin:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326   de  Dell Utility
/dev/sda2   *          12        4971    39841200    7  HPFS/NTFS
/dev/sda3            4972        6538    12586927+  83  Linux
/dev/sda4            9582        9729     1188810    5  Extended
/dev/sda5            9582        9729     1188778+  82  Linux swap / Solaris
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 2028 MB, 2028470272 bytes
212 heads, 32 sectors/track, 146 cylinders
Units = cylinders of 6784 * 2048 = 13893632 bytes
Disk identifier: 0x889121a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         146     1980864    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 32) logical=(0, 1, 1)
benjamin@benjamin-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=19293c52-7cce-459c-bf40-050976a14ffa /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=fce37ec2-3a59-47f8-9a3f-a1cbeceed7af none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


Sorry I didnt know how to contain the text in a div overflow... Ill do that next time if you can point out how. And yes, I used an existing parition within Vista before the install. After that though I installed Ubuntu and resize all my partitions with gparted on the livecd.

---

### Post by Rocket2DMn on 2008-03-26
OK, your menu.lst file still lines up with your fstab file, which means that grub is pointing to the right place.  I don't see anything else that would cause problems, so you should try the super grub disk, I hear it's very nice.
However, I am a little skeptical in this case because it seems to already be starting to load vista when something goes wrong, which means you may have screwed up vista when you resized your partition - maybe Pumalite knows something I don't.
If you have to end up reinstalling Vista, you can recover your data from the drive by mounting the ntfs partition in Ubuntu and copying over what you need.  Restoring the MBR from the Vista cd might work, but you will have to reinstall grub after that to be able to load Ubuntu.

---

### Post by solaceinsilence9 on 2008-03-26
Ill give supergrub a shot. I didnt think i messed anything up when i resized, I defraged first to make sure all my data was at the front of the partition and I can actually access the partition and see all the files from Ubuntu. If I need to reinstall is there anything I need to be wary of? I know you usually have to install Windows before Linux so does this mean I will  have to reinstall both?

---

### Post by Pumalite on 2008-03-26
Best thing to do is reinstall both; Vista first in sda1 and Ubuntu last. Make sure this time you FIRST allocate space for Ubuntu with Vista partitioner, then go and install Ubuntu in that new partition.

---

### Post by solaceinsilence9 on 2008-03-26
well it will have to be sda2. Dell puts EISA Utility Configuration partition as sda1 on the hard drive. its like 80mbs or something. Not sure exactly its purpose but I think it has something to do with the first boot out of the box. I heard it has some hd utilities on it also but you cant boot to it. Anyway, I guess Ill get started. Im going to try supergrub first. Ill post back in a little bit. Thanks for the help.

---

### Post by george182 on 2008-03-26
Hi, im new here!
And i'm having a similar problem.
I started with an original partition for windows xp. 
This worked fine until i decided to upgrade to linux (dapper drake) hoping for a single hard drive with two separate bootable OSs.
However at the moment, when the GRUB menu appears, I have the choice for both OSs, but only the linux one works(perfectly!).
But when i select windows, it freezes.
I tried typing the folowing into the GRUB command:

rootnoverify (hd0,0)
makeactive
chainloader +1
boot

and with makeactive and chainloader +1 the other way around as i saw written somewhere.
This also results in grub freezing
Please help!

---

### Post by Pumalite on 2008-03-26
Post:
sudo fdisk -lu

---

### Post by solaceinsilence9 on 2008-03-26
Ok well im back. Turns out I didnt have to do any of that. I just simply put in my Vista install disk and booted from it. I was about to reinstall Vista when I noticed a repair system option. Clicked that and the disk found the problem. Apparently the problem was the Vista partition was missing. Which makes sense seeing as how I moved the partition to another location on the hard drive. GRUB just didnt know where to look; it was looking at the old mounting point instead of the new one. Anyway I let it fix the problem, it restarted ran the Scan Disk to check for errors and BOOM, I can now load Windows from my GRUB menu. And best of all everything is STILL intact.  And I also still another 12gb of free space on that partition, that I might shrink down. So thanks to everyone for the help. But now on to the list of other problems that is plaguing my Ubuntu OS.:lolflag:

---

