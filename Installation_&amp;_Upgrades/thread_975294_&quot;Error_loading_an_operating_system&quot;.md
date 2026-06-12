---
title: "&quot;Error loading an operating system&quot;"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by pumex1990 on 2008-11-08
Hi,
I've just installed Ubuntu 8.10 (I saved the /home partition, and formated /) and after reboot there is an error "Error loading an operating system". But if I put Ubuntu CD and boot from it, than I can normally load an operating system if I take the "Start system from first hard drive" option.

I tried to repair grub with using Super Grub Disk, but it didn't help.

I also tried to install Ubuntu one more time, and at the last step of installation I change the place of Grub instalation for sd3 (which is my / partiton), but it still don't work.

I have already got a problem like that some time ago, and I fixed it by formating all of my partitions, but this time I'd like not to do it :)

What more informations do you need to help me? :)

---

### Post by bulldog on 2008-11-08
```
sudo fdisk -lu
``` in a terminal,and post the output on the forum please.

---

### Post by pumex1990 on 2008-11-08
```

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x90b190b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    86108399    43054168+  83  Linux
/dev/sda2       116230275   117226304      498015   82  Linux swap / Solaris
/dev/sda3        86108400   116230274    15060937+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x99a699a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    78140159    39070048+  83  Linux

```

:)

---

### Post by bulldog on 2008-11-08
If I read and understand correctly,you have two hdd's.
The question would be,which is your new install sda1 or sdb1.
The next thing is,on which hdd is GRUB installed.
And then,from which hdd are you booting.

It looks a little complex,but it isn't.
The bottem line is your menu.lst.
This is the place where GRUB finds the information it needs to boot any OS,if this points to a wrong partition,it won't boot.

So if you boot from sda,and GRUB is installed on this hdd,the boot line should point to hd0,0 but if you boot from sdb and GRUB is installed on this hdd it should point to hd1,0.

So take a look at your menu.lst or post the relevant part to the forum.

Your menu.lst can be found in /boot/grub/menu.lst

---

### Post by pumex1990 on 2008-11-08
So, here is my menu.lst:

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
# kopt=root=UUID=73e77171-1bf1-42c5-bece-5b6ceb088911 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=73e77171-1bf1-42c5-bece-5b6ceb088911

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		73e77171-1bf1-42c5-bece-5b6ceb088911
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=73e77171-1bf1-42c5-bece-5b6ceb088911 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		73e77171-1bf1-42c5-bece-5b6ceb088911
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=73e77171-1bf1-42c5-bece-5b6ceb088911 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		73e77171-1bf1-42c5-bece-5b6ceb088911
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I don't understand a lot from it, but maybe You can ;-)

---

### Post by bulldog on 2008-11-08
Just to clarify some things.
You do have two hdd's sda and sdb? right?
You have two times installed ubuntu? sda1 and sdb1 right?

Which hdd are you booting from sda or sdb?

Because everything in menu.lst looks normal and should boot.

You can try in a terminal```
sudo update-grub
```
and look carefully what it reports to you,specially if there where errors found.

---

### Post by pumex1990 on 2008-11-08
Yes, I've got two hard disks.
My Ubuntu is installed on sda, and on sdb I've only one partiotion, and I keep only my documents there, and there is no operating system.

But I've never got Ubuntu and the sdb drive.

here is the sudo update-grub output:

```
pumex@pumex-desktop:~$ sudo update-grub
[sudo] password for pumex: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

pumex@pumex-desktop:~$ 

```

---

### Post by bulldog on 2008-11-08
Okay,now we have to find out from which hdd you boot.
When GRUB is loaded select the line you want to boot.
Hit the 'e' key,you see something like (hd0,0)
Change this into (hd1,0) and hit the 'b' for boot.
Don't worry,this will not affect your menu.lst,it's just for one time purpose.
If this work,we can change the menu.lst.

---

### Post by pumex1990 on 2008-11-08
Hm, if I enter whre you told me to, I can't see anything that looks like (hd0,0). There are only some long numbers, as on this picture: [http://id.wklej.org/s/30032](http://id.wklej.org/s/30032)

---

### Post by Otustelija on 2008-11-08
Your menu.lst is messed up. Try changing the uuid lines to:

root (hd0,0)

If that doesn't work, try different numbers.

Edit:
You can also do the same from grub like bulldog suggested. Edit remove the first line and use the above instead.

---

### Post by pumex1990 on 2008-11-08
Hmm, I started to think, and I don't know if my first post was clear enough to explain my problem :)

Because IMHO my problem is that the Grub is not starting, not that the system from grub menu is not starting. Because this 'Error loading an operating system' shows before Grub started to load. And If I put my Ubuntu CD into computer, and then pick the last option from menu - boot from the first hird drive - than Grub starts normally, and Ubuntu is loading with no problems.

But the changes that you told me to do change AFAIK change only menu of Grub - so if I changed this long UUID number for (hd0,0), thare still was this 'Error loading an operating system' problem, but after I loaded Grub with using my Ubuntu CD there was also an 'Error 15' problem. But I changed (hd0,0) on (hd0,2) and it's working just like when instead of (hd0,2) there was this long UUID number.

So, to sum up:
Now I have root (hd0,2) instead of this long uuid ..., and if I use my CD to turn up grub, than it's working, but if there is no CD in the CD drive, then I've still got this "Error loading an operating system" - so i think that the computer is not able to load grub, not that grub is not able to load Ubuntu.

If I am wrong, correct :)

Uff, I hope that what I wrote here is understandable ;-) But what to do now? :)

And if it may be helpful - this error doesn't show in English, but at my language, while all Grub is in English :)

---

### Post by Otustelija on 2008-11-08
Oh, I misunderstood.

The last time you installed grub, you put in on sda3? You should try to reinstall it in MBR, since that's the place your BIOS will use first. Installing somewhere else is only a good idea if you have another boot loader in MBR - like the Windows one.

If you already had the problem when grub was in your MBR, it was probably on the wrong disk - it should be on the primary master disk. Another possibility is that it won't run, because you have the wrong partition flagged bootable.

---

### Post by pumex1990 on 2008-11-08
First I installed Grub on (hd0,0), and than - when it wasn't working - I installed it on sda3

So what should I do now? How should I 'reinstall it in the MBR'?

Sorry if it is a foolish question, but I'm not good at that ;-)

---

### Post by Otustelija on 2008-11-08
As I said, I'm not sure what the problem is. I would first try to change the sda3 partition (that's your / right?) to bootable. It should be rather easy if you can run a live cd with GParted (eg. ubuntu). If that fails, you could try changing the boot order of your hard drives from your BIOS. Change it back if it doesn't help.

If both of those fail, you should try to install grub again to MBR - ie follow these instructions: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Be sure to install on the disk that boots first from BIOS.

---

### Post by pumex1990 on 2008-11-09
Changing boot order in BIOS helped :) I don't know why it was messed up, if before reinstall everything was ok :)

Thanks for your help :)

---

