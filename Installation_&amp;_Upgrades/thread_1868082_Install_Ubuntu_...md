---
title: "Install Ubuntu .."
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by dameion123 on 2011-10-23
Hi all, 
 
I just signed up for this forum.. I have been trying to install ubuntu for a few days now but after a few days and much frustration I figured I would post here and see if I can get some help ... 
 
I am trying to install Ubuntu along side Windows 7. I can boot from either live cd or USB into Ubuntu trial area.  I can get into Gpart and make changes ... however when I go to install after making the changes I get an error "no root partition is defined"
 
I cannot set mount points in Gpart and would hope to do this in the install .. however once I get to the "no root partition is defined" it won't let me go any further until it is defined... in that install page (where everything stopped) there are no highlighted options to change anything.  
 
However ... something must have gone through in "one" of the installs that I did because I did have the dual boot loader at one point but I tried deleting it - now I have a computer that takes a long time to boot.  this is what my BCDedit looks like .. I'm not sure what all this means ... 
 
 
Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=C:
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
default                 {default}
resumeobject            {58b03381-fc9f-11e0-8ed3-96ad6127e306}
displayorder            {default}
toolsdisplayorder       {memdiag}
timeout                 30
Windows Boot Loader
-------------------
identifier              {default}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Windows 7
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {58b03383-fc9f-11e0-8ed3-96ad6127e306}
recoveryenabled         Yes
osdevice                partition=C:
systemroot              \Windows
resumeobject            {58b03381-fc9f-11e0-8ed3-96ad6127e306}
nx                      OptIn

 
In my Bios I can boot from 
 
Raid 
USB 
CD/DVD 
Lan 
 
I can install Ubuntu on a memory stick (usb) though.  When I get to the install part it will let me change HD to the stick and install it on there.  Of course this is not what I want.  It's like Ubuntu is not seeing the partitions which I create.  
 
Any help would be greatly appreciated.
 
Thanks 
 
Dameion

---

### Post by subhadip_sky on 2011-10-24
Welcome to Ubuntu forums. If you're installing Ubuntu from a live cd, you should set the mount point of the ext4 partition where you are installing your Ubuntu, as root which is shown by the character '/'. Click on 'Something else' at the point when you are asked what you want to do and you will be presented with a map of your hard disk, do the necessary partitioning there.

---

### Post by dameion123 on 2011-10-24
thank you for your reply .. 
 
initially when I tried to install Ubuntu (i've tried like 20 times now) I was allowed to continue on to a screen during the install (something else) whereby I could set the mount points.  However I must have botched that install (otherwise I would have installed it correctly) ... subsequent installs do not bring me to the point where I can set the mount points ( the install won't let me get that far ) ... I have been able to install Ubuntu to a flash drive however.  Sda 1 (at th install screen) shows no partitions in the table at all - all the buttons in this window do not allow me to change anything. 
 
Allocate drive space window I believe the window is called - picture of it here 
 
[http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/](http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/)
 
if i insert a flash drive and change to it ... the tables for that flash will show up and I can install to the flash drive ... I have checked other posts and will reboot with partition wiz bootable and will post results of  fdisk -lu once i figure out how ... not sure but maybe this might help in resolving this ... 
 
as well ... when in Bios my HDD boot is called   Raid Ary 1 
 
not sure if I'm giving enough information here ... if anything else is needed please let me know ... 
 
thanks again 
 
Dameion

---

### Post by dameion123 on 2011-10-24
here are some pictures I've taken of partition wizard, Bios and Gparted plus the window in which Ubuntu hangs.
 
hope these can help.

---

