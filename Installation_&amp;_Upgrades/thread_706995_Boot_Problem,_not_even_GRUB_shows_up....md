---
title: "Boot Problem, not even GRUB shows up..."
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by DeadlyOats on 2008-02-25
I'm doing a fresh install if Ubuntu 7.10 - upgrading from Ubuntu 7.04.  The installation completed, and it was time to start the system for the first time.  After POST, and after Adaptec RAID starts up, I get a blank, black screen with a flashing cursor where GRUB would announce what OS was starting up.

Except, that's it.  That's all I get - the flashing cursor and nothing else.  I suspect I might know the cause, but I'm not sure, and I don't have a clue as to how to fix it.

During installation it calls my Maxtor IDE hard drive a sda, and identifies it as a SCSI drive, but it is not SCSI, so shouldn't it be called hda or hd0 or something?

I partitioned my drives as follows:

on my Adaptec RAID card I have 4 Raptors in a RAID 5.  I partitioned it as 39999 for  /  using Ext 3, and the remaining space as /home/<username> using Ext 3;

on my Maxtor IDE hd, I have 699  for /boot using  Ext 2, 38362 for /home/<username>/extraspace, using Ext 3,  and 2048 for SWAP.

During install, it formats and installs the /boot files in the /boot partition on my Maxtor, but it's calling it sda and identifying it as SCSI1 (or something to that effect) even though the Maxtor is an IDE HDD conntected to the Primary IDE PATA connector of the motherboard.

As far as the hardware is concerned, it's the very same hardware I used for Ubuntu 7.04.  There have been absolutely no changes to any of the hardware.

Also, it's the very same partition scheme I've used for SuSE Linux, XandrOS Linux, and Ubuntu 7.04 Linux.  So, I figured the partitioning should not have been a problem, but now, with Ubuntu 7.10 ....?

How do I fix this?  :confused:

---

### Post by zvacet on 2008-02-25
If you press Esc button does grub show up?

---

### Post by DeadlyOats on 2008-02-25
I just tried pressing Esc on the keyboard.  Grub did not show up.

---

### Post by mittwit on 2008-02-25
If you have the install CD you could try booting from that. There is an option that enables you to login to a text screen. If you did that you could check your grub files. I think they are in /boot/grub 
I changed the menu.lst file in /boot/grub so that windows boots by default on my computer. Every time ubuntu does an update that requires a restart it replaces my menu.lst file with a new one that puts windows at the end of the list.
Maybe your menu.lst file needs adjusting

---

### Post by zvacet on 2008-02-25
@** mittwit**


> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

Do you have this lines in your menu.lst?If you don´t add it and below enter Ubuntu specifis.That way menu.lst will not be changed after Ubuntu updates.

---

### Post by DeadlyOats on 2008-02-25
I just booted the Install CD and am in the live CD mode.  What I'm looking at, in Nautilus,  is quite puzzling.  The drive that I created a partition for /Boot does not have the /boot directory in it.  The other drive, the RAID drive, has the /boot folder in it, but it is completely empty.  Not even "show hidden files " is showing any files in /boot.

So, not only did my /boot partition not create in the IDE drive *I* selected, but it is empty.

I guess that means re-install?  If that's what it means, then what about my other problem.  Ubuntu is identifying my IDE HDD, connected to the Primary IDE controller of my mobo, as a SCSI drive, and is labeling it as sda or some kind of SCSI name, instead of hda or some kind of IDE name.

I think this is why the /boot folder created in the wrong drive, and why it is empty.

Of course, I could be wrong, I'm really a Linux n00b.  I've been using it for a long time, but I've been GUI-ing everything and haven't really looked under the hood.

By the way, I want to express my thanks for you guys' help up until now.  I hope you'll bear with me on this and keep the ideas coming.

---

### Post by DeadlyOats on 2008-02-25
Never mind my previous post.  I found the partition which I selected for /boot.  I found the menu.lst file.

For some reason, happy faces appear in the section just below.  It should be a number 8 between parenthesis ( ), with no spaces.



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
# kopt=root=UUID=204adfaa-c995-4541-9345-daea66b78acd ro

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
kernel		/vmlinuz-2.6.22-14-generic root=UUID=204adfaa-c995-4541-9345-daea66b78acd ro quiet splash
initrd		/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=204adfaa-c995-4541-9345-daea66b78acd ro single
initrd		/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

So, anything wrong with it?  This is not a dual boot machine, It's all Ubuntu - or I'd like it to be.

---

### Post by mittwit on 2008-02-26
Hi again,
I no expert either, but here are some things you could try:

In your menu.lst find the following:
```

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

```
Put a # in front of hiddenmenu That way if grub is loading you will see your boot options.

My menu.lst as the following ubuntu options:
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bb026f8d-74cb-4a5b-ba3c-7af18c0468fa ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bb026f8d-74cb-4a5b-ba3c-7af18c0468fa ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

```

The kernel value points to the file vmlinuz-2.6.22-14-generic which is in my /boot directory on (hd1,0)
In the same way the initrd value points to the file initrd.img-2.6.22-14-generic which is in my /boot directory on (hd1,0)
Your menu.lst will look for those files in the root directory of your (hd1,0)
```

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd1,0)
kernel /vmlinuz-2.6.22-14-generic root=UUID=204adfaa-c995-4541-9345-daea66b78acd ro quiet splash
initrd /initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd1,0)
kernel /vmlinuz-2.6.22-14-generic root=UUID=204adfaa-c995-4541-9345-daea66b78acd ro single
initrd /initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd1,0)
kernel /memtest86+.bin
quiet

```
You should check that that is where they are. If they are then I am not sure what is going on. The only other thing you could check is that the boot order in your bios is correct.
Good luck.

---

### Post by froy02 on 2008-02-27
First:  It does not matter what Ubuntu designates your hard drives for booting purposes, to grub they will all be (hdx), x is number from 0.  
Your menu.lst indicates that Ubuntu is installed on the 2nd drive on the first partition (hd1,0).
Verify that by booting with a live CD and go to a terminal.
Code: sudo grub
The grub prompt comes up.
Code: find /boot/grub/stage1
If it returns (hd1,0) then your menu.lst is accurate and I am not sure what could be done to fix it.  
If it returns a different drive then you have to re-install grub using the instructions here: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by sistoviejo on 2008-02-27
One other thing... You can use a partition manager to choose which partitions are flagged as bootable.
Maybe the wrong partition has the flag.

More info:
[http://ubuntuforums.org/showthread.php?t=289605](http://ubuntuforums.org/showthread.php?t=289605)
[http://kerneltrap.org/node/6033](http://kerneltrap.org/node/6033)

---

### Post by DeadlyOats on 2008-03-12
I tried all of the solutions you guys posted.  No Joy on all of them.  I installed SuSE 9.1, SuSE 10.0, and even XandrOS 2.5 with success.  I figured I had a corrupt Install CD, so I figured I'd give Kubuntu a try.  I downloaded Kubuntu and burned the iso using SuSE 10.0.  Same problem occurred.  So, I could not figure out what was wrong with the Ubuntu or Kubuntu installs.

I ended up deleting all of my partitions and re-creating them the exact same way.  Then I tried installing Kubuntu again.  This time it worked.  The problem is solved, but the solution is not known.

Thanks for all of your help, guys.

Oh, yeah.  One last note.  SuSE 9.1 & 10.0, and XandrOS 2.5 all correctly identify my Maxtor ATA drive as hd0 or hda or whatever, but Ubuntu and Kubuntu continue to show my Maxtor PATA drive as sda or sdb.  Ubuntu still ID's my PATA drive as a SCSI drive.  That, to me is a problem.  Whether the problem had any bearing on my grub issue is unknown to me, but it is something that may need looking into.

I'm having a ton of trouble updating Kubuntu after the install.  Adept complains that it cannot commit the changes, and quits.  When I reboot, the grub issue comes back.  I end up having to re-install Kubuntu.  I'll try Kubuntu one last time, then I'm gonna give Ubuntu one last shot before I go back to SuSE Linux.

I really liked Ubuntu 7.04, but it's not being supported anymore, which is why I'm trying to switch to 7.10, but it is quite problematic for me.  (I posted from Kubuntu Live CD while the install was taking place.  Install is completed, so I'm going to re-boot now.  Wish me luck.)

---

