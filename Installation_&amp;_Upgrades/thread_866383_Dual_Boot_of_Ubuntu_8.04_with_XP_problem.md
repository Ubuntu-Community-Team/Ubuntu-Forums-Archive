---
title: "Dual Boot of Ubuntu 8.04 with XP problem"
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by klm33 on 2008-07-21
Folks,  I have XP prof installed and wanted to do a dual boot with Ubuntu 8.04 and after installing Ubuntu my machine olny boots to XP prof.  Many years ago on this same disk I had installed a redhat version of Linux and ended up uninstalling it and somehow disabling the boot manager (Grub?).  I think that my problem is with the MBR and cannot find how to enable Grub or a boot loader that I have been reading about in these forums.  The ver 8.04 install seemed to have happened but I can only use Ubuntu from the CD-ROM and not access the partition it was installed on.  I have tried making the boot sector "active" but the system cannot find an operating system.  I know just enough to be dangerous.  Please make some recommendations.   Thanks -- Ken

---

### Post by logos34 on 2008-07-21
I suggest reinstalling ubuntu.  Check in the Bios that there is no MBR 'write-protect' feature enabled.

When you get to step 7 "Ready to Install' screen, press 'Advanced' lower right and verify that install grub booloader option box is checked and set for '(hd0)'.

---

### Post by klm33 on 2008-07-21
Thanks for your help; I'll try it.....Ken

---

### Post by klm33 on 2008-07-22
Logos34,

Tried your suggestions:  Bios ok, reinstall still no boot manager or access to Ubuntu.  I suspect that when I installed Redhat five years ago and then uninstalled it that I did something to stop bootmanager from working and I don't remember how to get it working again.  I also tried reformatting the boot sector and setting /dev/sdb2 ext3 /boot as the bootloader option during step seven and that also did not work.  I go directly to XP Pro and do not pass go and do not collect $100.....  Any suggestions?
Ken

---

### Post by xen-uno on 2008-07-22
You can look at menu.lst (see /boot/grub/ dir) in the Ubuntu partition from Windows. Make sure the (hd x,x) parameters are correct for all un-commented lines. See mine on post #5 [_*here_*](http://ubuntuforums.org/showthread.php?t=865445). Windows and the boot is on disk 1, partition 1 (hd0,0). Ubuntu is on disk 2, partition 3 (hd1,2).

edit ... just saw your "no boot manager" ... have you tried using a SuperGrub disk yet?

---

### Post by logos34 on 2008-07-22
> **klm33 said:**
>  and setting /dev/sd[COLOR=Red]**b**[/COLOR]2 ext3 /boot as the bootloader option during step seven and that also did not work. 

wait--do you have TWO hard disks?  Please clarify...because that would explain the trouble

from the live cd, run

sudo fdisk -l

post it

---

### Post by klm33 on 2008-07-24
Yes, I actually have four hard drives.  Ken

---

### Post by logos34 on 2008-07-24
> **klm33 said:**
> Yes, I actually have four hard drives.  Ken

Only four...

Why didn't you mention it?  Could have saved yourself a lot of fuss.

Set the drive with ubuntu first in the Bios hard disk boot priority, then boot from the live cd and edit menu.lst so the root lines read (hd**0**,x)--if you have a separate /boot then the partition 'x' should refer to that rather than / partition.  Reinstall grub to that drive's MBR. (see my sig).

---

### Post by klm33 on 2008-07-24
Need a little more help; I removed one drive and now have three.  I booted with the Ubuntu disk after setting my primary (C:XP with Ubuntu and swap partitions) hard drive as booting just after the DVD/CD Rom boot in the Bios setup.  I then used the file browser in Ubuntu to search for the "menu.1st' file to edit it and could not find it on any hard drive partition.  this is what is on my system:
415MB /dev/sdb2/  ext3 /boot -- 42GB /dev/sdb1 fat32 (my WIN XP) -- 71GB /dev/sdb3/  extended -- 68GB /dev/sdb5  ext3 (Ubuntu) -- 2.9Gb /dev/sdb6  Linux swap

I know it is very hard to solve a problem when you don't know all the facts.  

I know enough about Windows and OS/2 to be dangerous and have friends ask for help over the phone often and without seeing what they are describing it is like being blind. 

 I've got all my data on the old system that I want to convert to Linux and have a new PC devoted strictly to Win XP and Photoshop for speed in editing 150 - 200 MB images.  They are connected via an ethernet cable.  

I still have a gut feeling that when I uninstalled Redhat Linux five years or so ago that I had trouble with dual boot still coming up even though I had only one operating system.  I am not sure what I did back then to have the system boot directly to Windows XP Pro.

Also, could you elaborate on what 'see my sig' means?

Really appreciate your help and tenacity.   Thanks Ken

---

### Post by ray_niblock on 2008-07-24
KLM33.
I may be facing a similar problem.
BTW.  'See my sig' just means:  see my signiture below.  Some people put a fancy signature at the end of each post as a quote from some esoteric missive or the like.  Normally harmless and interesting.  In this case the poster has helpfully included some hyperlinks to various web sites as his signature.  So I guess one of those will link to a useful URL that will give some relevant information.

When you find the solution, I would love to know as I have just installed XP on a second hdd whilst my ubuntu disc was disconnected and would now like to know how to edit my menu.1st file etc to be able to include this winxp disc in the grub bootloader screen:  Which I'm guessing is where you are (?).

I've had a bash with Super GRUB disc and, to be honest, find it a bit scary as, even though I have backed all my data up on my ubuntu disc, I don't want it not to be able to boot again.  Also, the Super GRUB is a bit difficult, imo, to be able to easily fathom.

Ray

---

### Post by logos34 on 2008-07-24
> **klm33 said:**
> Need a little more help; I removed one drive and now have three.  I booted with the Ubuntu disk after **setting my primary (C:XP with Ubuntu and swap partitions) hard drive as booting just after the DVD/CD Rom** boot in the Bios setup.  I then used the file browser in Ubuntu to search for the "menu.1st' file to edit it and could not find it on any hard drive partition.  this is what is on my system:
415MB /dev/sdb2/  ext3 /boot -- 42GB /dev/sdb1 fat32 (my WIN XP) -- 71GB /dev/sdb3/  extended -- 68GB /dev/sdb5  ext3 (Ubuntu) -- 2.9Gb /dev/sdb6  Linux swap

no, that's the **device** boot order--there's a submenu for hard disk boot priority.

Menu.lst normally should be in sdb2, your separate /boot, but then things don't appear normal here.  You can try generating another one by running grub-install with /boot mounted.  So if sdb2 is mounted at, say,  '/media/disk', you would do:

**sudo grub-install --root-directory=/media/disk /dev/sdb**


> **ray_niblock said:**
> I have just installed XP on a second hdd whilst my ubuntu disc was disconnected and would now like to know how to edit my menu.1st file etc to be able to include this winxp disc in the grub bootloader screen

[http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk)

---

