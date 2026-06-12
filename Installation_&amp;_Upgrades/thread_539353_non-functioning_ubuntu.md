---
title: "non-functioning ubuntu"
date: 2007-08-31
forum: Installation &amp; Upgrades
---

### Post by ubuntolover2000 on 2007-08-31
:(I installed Ubuntu in my PC, which already had Windows XP Professional, about three months back and was happy with it.   However, last week, due to a sudden unexpected power failure, my computer turned off (i was not using any UPS).  When  power supply resumed, I turned on my the PC. However, UBUNTU did not load and was showing some error message.

so the next morning, i brought the UBUNTU installation CD and booted from CD.  Thereafter, I installed ubuntu again in my PC and so far it is working fine.

However, when i start my PC i noticed that it is offering three alternative operating systems:

First is the recently installed Ubuntu.
The second is the Ubuntu installed three months ago which is showing error messages while booting. 
The third is the Windows XP.

My questions are:

1. Is the non-functional Ubuntu taking up disk space? 
2. If yes, how to delete this non-functional Ubuntu?
3.Is there a way to make this non-functional ubuntu operational again?

I shall be extremely grateful for the answers.


Ubuntolover2000

---

### Post by chewearn on 2007-08-31
First, we need figure out your harddisk setup, i.e. how many harddisks you have, how are they partitioned, where ubuntu and windows are installed etc.  If you are unsure about how to answer these, then boot into the latest ubuntu installation, open a terminal, and run the following commands:

```
sudo fdisk -l
cat /boot/grub/menu.lst
```Post the output from these commands, and we can find out what is going on.

---

### Post by ajgreeny on 2007-08-31
It sounds as if your install was clever enough to find the first broken ubuntu on the machine and keep this information in memory until it set up grub, even though you then probably overwrote the original.
It happened to me once when I installed Linux Mint, based on ubuntu on a second hard drive on my machine and this was installed over a previous install on that disk of ubuntu dapper.  There was no trace of the old install left except this entry on grub, I know this from my **fdsik -l** output, so I just edited the grub menu.lst and no problems came from it at all.

---

### Post by ubuntolover2000 on 2007-08-31
Dear Alta Vista

I have two hard disks, the windows sits in hda1 partition and ubuntu sits in hda3 partition. This much I know. Is it enough or i have to give more info?

Ubuntolover2000

---

### Post by ubuntolover2000 on 2007-08-31


dear ajgreeny,

i got yr solution. can u please suggest how to edit this grub list?


Ubuntolover2000

---

### Post by ajgreeny on 2007-08-31
We do need to see your output from **sudo fdisk -l** before going further just to make sure you are not wasting any disk space, one of your first concerns in your post, so copy that output and then we'll go to the edit if it is the right thing to do.

When you get to that point it will be **gksudo gedit /boot/grub/menu.lst** in terminal and then edit the file and save it, but we need to make sure we get rid of the correct entry, and not make your system unbootable.

---

### Post by ubuntolover2000 on 2007-09-01
dear Astalavista and ajgreeny,

when i ran the 'sudo fdisk -l' , in the terminal, i got the following:-

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/hda2            2551        5404    22924755    f  W95 Ext'd (LBA)
/dev/hda3            5405        7297    15205522+  83  Linux
/dev/hda5            2551        4309    14129136    7  HPFS/NTFS
/dev/hda6            5316        5404      714861   82  Linux swap / Solaris
/dev/hda7   *        4310        5265     7679038+  83  Linux
/dev/hda8            5266        5315      401593+  82  Linux swap / Solaris

Partition table entries are not in disk order


  When I run 'cat /boot/grub/menu.lst' command; i get :-


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
# kopt=root=UUID=1c3ceedc-4ad7-4178-9dcc-e182ec3de1c6 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=1c3ceedc-4ad7-4178-9dcc-e182ec3de1c6 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=1c3ceedc-4ad7-4178-9dcc-e182ec3de1c6 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=1c3ceedc-4ad7-4178-9dcc-e182ec3de1c6 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=1c3ceedc-4ad7-4178-9dcc-e182ec3de1c6 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,6)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title           Ubuntu, kernel 2.6.20-16-generic (on /dev/hda3)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=422118dd-9700-458a-b149-c4cc196d9211 ro quiet splash 
initrd          /boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title           Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/hda3)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=422118dd-9700-458a-b149-c4cc196d9211 ro single 
initrd          /boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title           Ubuntu, kernel 2.6.20-15-generic (on /dev/hda3)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=422118dd-9700-458a-b149-c4cc196d9211 ro quiet splash 
initrd          /boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title           Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/hda3)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=422118dd-9700-458a-b149-c4cc196d9211 ro single 
initrd          /boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title           Ubuntu, memtest86+ (on /dev/hda3)
root            (hd0,2)
kernel          /boot/memtest86+.bin  
savedefault
boot
 


PLEASE HELP ME.
UBUNTOLOVER2000

---

### Post by ubuntolover2000 on 2007-09-01
Here is ubuntolover2000 again,

when i try to start the non-functional ubuntu, i get the follwoing error message while booting up:-

"An automatic file system check (fsck) of the root filesystem failed.  a manual fsck must be performed, then the system restarted.  the fsck should be preformed in maintenance mode  with the root file system mounted in read-only mode"

in the light of above message, could anyone advise me what i should do?
Ubuntolover2000

---

### Post by merlinus on 2007-09-01
From /boot/grub/menu.lst and fdisk, it looks like (hd0,2) is the old install.

You might try placing a # in front of those lines at the end of the file.

Then if ubuntu boots correctly, you can delete the (hd0,2) stanzas and that partition (hda3) might as well be reformatted and used for something else, such as /home.

-merlin

---

### Post by ubuntolover2000 on 2007-09-01
My dear merlinus,

thanks 4 ur reply. but could u please tell exact i should write in the terminal?

another point i like to share with all

Just half an hour back i booted  from the ubuntu cd.  when i opened 'Computer' from 'Places', i noticed that it is showing, along with the two installed hard disks, two additional disks, named 'disk' and 'disk-i'.  It is apparent to me that in the 'disk' portion contains the old ubuntu which is no longer operational.  'disk-i' contains the newly installed obuntu.  'Disk' eats up around 15 GB and 'disk-i' eats up around 8 GB of space.

so in other words, how should i uninstal this 'disk' so that the space used by it can be used elsewhere.  

Ubunto lover2000

---

### Post by merlinus on 2007-09-01
> 
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title           Ubuntu, kernel 2.6.20-16-generic (on /dev/hda3)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=422118dd-9700-458a-b149-c4cc196d9211 ro quiet splash 
initrd          /boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title           Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/hda3)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=422118dd-9700-458a-b149-c4cc196d9211 ro single 
initrd          /boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title           Ubuntu, kernel 2.6.20-15-generic (on /dev/hda3)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=422118dd-9700-458a-b149-c4cc196d9211 ro quiet splash 
initrd          /boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title           Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/hda3)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=422118dd-9700-458a-b149-c4cc196d9211 ro single 
initrd          /boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title           Ubuntu, memtest86+ (on /dev/hda3)
root            (hd0,2)
kernel          /boot/memtest86+.bin  
savedefault
boot


Place a # in front of all these lines that do not have one.  Then reboot.  If no problems, then delete them.

You can edit the file this way:

```

gksudo gedit /boot/grub/menu.lst

```As for the old install partition, you can format it using gparted live cd and then use the space for storage.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by ubuntolover2000 on 2007-09-03
dear merlinus,

thanks for your solution. i am no longer seeing the non-functional ubuntu when i boot. thanks.

as for the using of gparted live cd, i am studying the materials i got from the gparted website and and i shall do it. 

thanks.  may death come to your enemies.


Ubuntolover2000:)

---

