---
title: "First Boot after install fails after GRUB"
date: 2007-03-29
forum: Installation &amp; Upgrades
---

### Post by FakeFrowns on 2007-03-29
I couldn't  find any information about this problem right off so here it is:

I am installing ubuntu 6.10 on a system. It will boot and run the live cd perfectly.  I run the installation program and it goes through and completes without an error.  It then reboots and I take the cd out.  The Grub loader comes up and asks me if i want to run Ubuntu or the mem test, and all the normal options.  No matter what i choose it won't boot.  I get an error saying that it is unable to mount the selected drive.  Anyone know what might be causing this?

Other information that might be important:

I am already running windows XP on the computer.  ubuntu is being installed to a seperate HD completely.  The ubuntu drive is the second HD referred to as (hd1) of course.  I had the installer load the GRUB to that driver rather than my XP drive because i didn't want it messing up my working XP install.  The bios is just checking HD1 as the first boot drive instead of HD0.  I'm not sure if that could be any part of the problem.

Let me know if you've got any ideas. Thanks

---

### Post by john_spiral on 2007-03-29
Does either Ubuntu or XP boot?

Sounds like you will need to edit the /boot/grub/menu.lst  file (can be done via the LiveCD).

boot from the live CD and post the results from a terminal with the following command:

**more menu.lst ** 

(once in the /boot/grub/ directory)

and
 
**sudo fdisk -l**

come back to us

johne

---

### Post by esodin on 2007-03-29
I think there might be a pretty straight forward answer to your problem. Let me recap to see if I got this right:
- You installed Ubuntu while your Linux HD (L-HD was the second in the boot sequence; thus the id (hd1).
- You then went into BIOS and changed LHD (rather than XP-HD) to the first boot drive.
- GRUB loads, but Ubuntu does not.

If this is correct the problem has a straight forward solution: When you changed the boot sequence (in BIOS) your L-HD becomes (hd0). GRUB is trying to start Ubuntu from (hd1), witch is now your XP-HD.

A temporary fix is to move to the Ubuntu item in the menu and hit “e” when the GRUB menu comes up (this will allow you to edit the commands executed when you select “Ubuntu” )

There should be 3-5 lines. The first one set’s the root and probably reads:  **root (hd1)** Change it so it reads (hd0). (Pressing “e” will allow you to edit the highlighted line; enter will confirm the edit). Check the other lines for references to (hd1) and change them to (hd0). When you are satisfied that all (1 to 3) references to (hd1) has been changed to (hd0) you should hit “b” for boot. If all is done correctly Ubuntu should now boot.

If you choose to keep the setup (using BIOS to change OS) you will need to edit the GRUB menu permanently. The GRUB menu is located in **/boot/grub **and called **menu.lst** – you will need to be a root user to save any changes you make. 

You should not be worried about running both Ubuntu and XP from GRUB. GRUB is an excellent boot loader. I use it to choose between Ubuntu, XP and Vista. If you make a mistake it is quite easy to reinstall the XP boot loader as well. 

Good luck!

---

### Post by FakeFrowns on 2007-03-29
to answer your first question - neither will boot from GRUB.  Windows still works if i boot direct to that HD.

Booting from the live cd there is no folder /boot/grub/  Do i have to do something to browse the boot folder on the ubuntu install on the HDD instead of the files on the live cd?

sudo fdisk -l returns this:
ubuntu@ubuntu:/$ sudo fdisk -l

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       13054   104856223+   7  HPFS/NTFS
/dev/hda2           13055       30401   139339777+   7  HPFS/NTFS

Disk /dev/hdc: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        3497    28089621   83  Linux
/dev/hdc2            3498        3649     1220940    5  Extended
/dev/hdc5            3498        3649     1220908+  82  Linux swap / Solaris
ubuntu@ubuntu:/$

---

### Post by dcstar on 2007-03-29
> **FakeFrowns said:**
> to answer your first question - neither will boot from GRUB.  Windows still works if i boot direct to that HD.

Booting from the live cd there is no folder /boot/grub/  Do i have to do something to browse the boot folder on the ubuntu install on the HDD instead of the files on the live cd?

You must mount your hard disk with Ubuntu on it, and navigate to the correct place on that.

---

### Post by john_spiral on 2007-03-29
boot from CD

get into terminal:

**sudo mkdir /mnt/linux_drive**

**** THE ABOVE COMMAND CREATES A DIRECTORY CALLED 'linux_drive' ****

**mount dev/hdc1 /mnt/linux_drive -w**

**** THE ABOVE COMMAND MOUNTS YOUR LINUX DRIVE SO YOU CAN EDIT FILES ****


**gedit /mnt/linux_drive/boot/grub/menu.lst**

this will allow you to edit the problem file the gnome editor.

---

### Post by FakeFrowns on 2007-03-29
Ok, can't believe i didn't do that before asking. dumb question sorry.

here's the results:

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
# kopt=root=UUID=d2603a78-09bc-4360-9793-0a34550de44f ro
# kopt_2_6=root=/dev/hdc1 ro

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

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdc1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdc1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet
boot

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
chainloader     +1



-------------------------------------------------------

the fdisk results i added to the last post.

---

### Post by john_spiral on 2007-03-29
to get the Ubuntu beast working, change 

root (hd1,0)

to:

root (hd0,0)

---

### Post by esodin on 2007-03-29
Please see my post above. When you change the boot sequence in BIOS to boot from your Linux HD your linux HD becomes (hd0)  It is no longer (hd1)

---

### Post by john_spiral on 2007-03-29
to get Windows going:

change:

title Microsoft Windows XP Professional
root (hd0,0)
savedefault
chainloader +1


to:

title Microsoft Windows XP Professional
rootnoverify (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
savedefault

this will set Windows as default os

---

### Post by john_spiral on 2007-03-29
This issue has been a long standing bug in the Ubuntu install. 

I've got my system set-up exactly like yours -not allowing the Ubuntu installer to touch my Win drive.

has this been resolved in the latest incarnation of Ubuntu?

---

### Post by esodin on 2007-03-29
> **john_spiral said:**
> This issue has been a long standing bug in the Ubuntu install. 

I've got my system set-up exactly like yours -not allowing the Ubuntu installer to touch my Win drive.

has this been resolved in the latest incarnation of Ubuntu?

The problem comes from changing the HD boot sequence in BIOS. If you set the hd that you intend to use for Ubuntu as the first drive to boot from (in BIOS) BEFORE you boot from the Live CD and install Ubuntu - the menu.lst file would have been constructed correctly. I found out the hard way. :)

---

### Post by FakeFrowns on 2007-03-29
You guys were right. Works like a charm.  Thanks a ton!

---

