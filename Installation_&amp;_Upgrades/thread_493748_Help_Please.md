---
title: "Help Please"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by enzopol on 2007-07-06
Hi,

Thank you for taking time to read my plea, and thank you in advanced for your help.

I am not completely new to Ubuntu having installed 7.04 in at least 5 pc for friends, and twice for myself at the office.  Up to today, i was doing great and enjoying freedom.

My problem (sorry I did not really pay too much attention when I started because I was confident that installation  is now routing for me.

My PC:

self assembled PC
- MD: Intel 845 Perl, P4 3.0
2 HD: 1st is Sata 250 (partitioned 150Gb Drive C, 100Gb Drive D
          2nd is a regular (forgot the term) 80Gb - 40Gb Drive E, 40Gb drive F

I installed Ubuntu from a cd and noted that instead of recognizing the Sata drive (the one with Windows installed), the default was the second hard disk.

Since it was the default I continued the installation process without a problem.  

However, after the reboot and remove the installation cd, i got a message (sorry forgot the exact term) saying unknown operating system.

My guess was since windows was in the sata hd, and since i was not given the option to import settings, i may have installed in the wrong drive.

I boot up the pc using the Ubuntu Cd and again repeated the installation but this time i chose the second option/Hardisk instead.

This time, i was given the option to import setting and again, installation when normally until the end.

Sadly, after the reboot, i still am unable to boot up the pc normally.

Having said all the above, i hope you are able to guide me on the exact steps to do.  By the way, i tried navigating to the hard disk after booting up from the CD but i was not able to reach the windows files (my original before partitioning Drive C:)

Help me please 

Respectfully,

Renz
(enzopol@yahoo.com)

---

### Post by aquavitae on 2007-07-06
Do you get as far as grub, of do you get the message before that?

Boot of the cd, open a terminal, and type
```
sudo fdisk -l
```
What's the output?  It should show your disks, and what the partitions are on them.  From this you'll be able to see where windows is (look for the fat or ntfs partitions) and where linux is (look for ext3, reiser or linux swap partitions).  What does it look like?

---

### Post by enzopol on 2007-07-06
Thank you for your reply.  Please see the following:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100        9729    37190475    f  W95 Ext'd (LBA)
/dev/sda5            5100        9729    37190443+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30024   241167748+  83  Linux
/dev/sdb2           30025       30401     3028252+   5  Extended
/dev/sdb5           30025       30401     3028221   82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by aquavitae on 2007-07-06
So it looks like windows is on /dev/sda and linux is on /dev/sdb.  
When you boot, do you get as far as grub?  
Which drive is your pc set to boot from (in the bios settings)?

---

### Post by enzopol on 2007-07-06
Hello again and thanks for your help.

Since my last post, i tried making changes to the grub.  I am now able to reach the grub portion (earlier i got the error message soon after the bios boot).

However, i am not clear on what to edit in the grub.  I am not getting a error 17 : cannot mount selected partition 

In the Bios, my pc is set to boot from the 250Gb:

    Disk /dev/sdb: 250.0 GB, 250059350016 bytes
    255 heads, 63 sectors/track, 30401 cylinders
    Units = cylinders of 16065 * 512 = 8225280 bytes

    Device Boot Start End Blocks Id System
    /dev/sdb1 * 1 30024 241167748+ 83 Linux
    /dev/sdb2 30025 30401 3028252+ 5 Extended
   /dev/sdb5 30025 30401 3028221 82 Linux swap / Solaris  

I wont make further changes for now and will wait online for your next instructions/guide.

Thank you again

Renz

---

### Post by aquavitae on 2007-07-07
Sorry, Haven't been able to get to internet for a while!

Can you post the contents of the file /boot/grub/menu.lst - its the configuration file for grub.

---

### Post by enzopol on 2007-07-07
Thank for your help.

I hope i am not in trouble as i am beginning to believe.

Waiting,

Renz

PS:  Could we possibly chat YM   enzopol

Following is the contents of the menu.lst



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
# kopt=root=UUID=bf4e3140-ad97-4465-acb9-1c4aac22b78f ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=bf4e3140-ad97-4465-acb9-1c4aac22b78f ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=bf4e3140-ad97-4465-acb9-1c4aac22b78f ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by aquavitae on 2007-07-07
Hmm, a bit confusing.  What I usually do when installing is to unplug my windows drive, then I know its reading the right one.  Then its just a case of adding windows to grub.lst.  What I'd suggest now is to do that.  We could try to sort it all out, but I think reinstalling will be faster and less painful!  
1. Unplug the drive that has windows, set the other to be single master (or CS, whatever to make it the primary first disk.  I assume if your PC's self assembled you know what I mean.)  
2. Boot off the live cd, install ubuntu to the (now only) drive.  Once installed, check that the installation has worked.
3. Plug in the windows drive as slave.  Boot
4. Boot into linux.
5. In a terminal type the following:
   sudo gedit /boot/grub/menu.lst
6. At the bootm of the file, add the following lines:
   title Windows XP
   map (hd1) (hd0)
   map (hd0) (hd1)
   chainloader (hd0,0)+1

Hopefully all will be sorted out.

---

### Post by aquavitae on 2007-07-07
> PS: Could we possibly chat YM enzopol
(yahoo, I assume - I don't always get the abbreviations ;D)
aquavitae69

---

### Post by enzopol on 2007-07-08
Hello again,

Start from scratch indeed is the easiest to do BUT, I have close to 180Gb of data in the same hard disk.

I tried removing the 250Gb Hard disk and installed it as a slave in another PC only to find out that the original partiton has been deleted.  How Why - it is strange, it should NOT happen, but it DID.

Start from scratch it is BUT again, before doing that, I am going to try all possible means to restore the partition, and restore whatever files I can salvage.  In the meantime, i decided to get myself a new Hard disk, install Ubuntu first then install windowz.  I only use windowz for a single Access Application.

Anyone reading this message, and have ideas, PLEASE share your expertise.  Others will learn from our experiences, and benefit likewise.

PLEASE recommend partition recovery tools, or any ideas on how to reverse the unfortunate fate my PC has gone through.

Many thanks just the same,

Renz
enzopol  at  yahoo  dot  com

---

### Post by aquavitae on 2007-07-08
Somewhere along the line I've got confused - which drive should have windows?  The 250 or the 80?  From your previous posts I got the impression it was the 250, so I'm assuming that's right.

> 
I tried removing the 250Gb Hard disk and installed it as a slave in another PC only to find out that the original partiton has been deleted.  How Why - it is strange, it should NOT happen, but it DID.
I must be going blind - only now have I seen that from your output of "fdisk -l" linux was installed on the 250G, but the 80G still has windows partitions.  So your original surmise was correct - ubuntu installed on the wrong drive.  As for getting the data back.... I don't know if you can, but you might be able to do something clever with a low level analysis.  Maybe someone else can help more here, but if you know what your original partition table looked like, you could restore it.  This wouldn't restore the data that's already been overwritten though.  Try a google search for recovering lost partitions - I think there's something somewhere.

> In the meantime, i decided to get myself a new Hard disk, install Ubuntu first then install windowz.
I'd still suggest installing each on a separate drive (not sure if this is what you meant :D)  Your other drives shouldn't be physically damaged.
> I only use windowz for a single Access Application.
Jumping ahead a bit.... but have you though of using Crossover Office (think I got the name right) to do this?  Alternately installing windows in a virtual machine?  Just ideas, might be worth looking into.

---

### Post by enzopol on 2007-07-09
Me again saying hello,

I have my system up and running by a new hard disk while i try to find a way to recover data from my old hard disk.

Just wanted to say Thank You So Much for your assistance.

Respectfully,

Renz

---

### Post by aquavitae on 2007-07-10
No problem.  If you need any more help, make a post, or you can PM me if you think it something I'll be able to help specifically with.

---

