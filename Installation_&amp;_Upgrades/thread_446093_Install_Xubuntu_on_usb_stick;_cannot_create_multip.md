---
title: "Install Xubuntu on usb stick; cannot create multiple partitions?"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by dgel on 2007-05-16
Hi

I'm trying to install xubuntu on my usb stick and so far i've been able to figure out it should be possible theoretically. However, before installing i want to make partitions on the disk with gparted (i like it better than the partition editor used during during the installation)
When I try to create the extended  partition, which is necessary as it only suports 1 primary partition, it states:
"loop disk labels do not support extended partitions"

What does this mean? Is it impossible to create partitions on my flash disk? Its a 4 GB micro disk by Hitachi btw.
Or is there a possible workaround for this?
any help would be appreciated.

[EDIT]
Forgot to ask, if it is possible, does anyone know how to set an MBR for it as well?
[/EDIT]


Na-Fiann

---

### Post by mrbig1492 on 2007-07-15
I found this link that describes what seems like a useful process for this endeavor. 

[http://xubuntublog.wordpress.com/2007/06/17/ubuntu-feisty-on-your-usb-drive-finally/](http://xubuntublog.wordpress.com/2007/06/17/ubuntu-feisty-on-your-usb-drive-finally/)


However, I have already run into a snag when trying to do it myself.  When I get to this part:
mrbig@mrbig-ME-262:~$ sudo mkfs.vfat -F 32 -n UbuntUSB /dev/sda1
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: /dev/sda1 contains a mounted file system.
mrbig@mrbig-ME-262:~$ 

it stalls with the complaint about the mounted file system.  Of course, if I unmount the partition, then there is no /dev/sda1 to find.

Am I stuck in "Catch-22" land?

TIA for any help given.

Ernie

---

### Post by ThunderBob on 2007-07-24
If you havent already try 

umount /dev/sda1

then try mkfs.vfat -F 16 -n UbuntUsb /dev/sda1

Also make sure that you have created the 2 partitons already before using the mkfs command.

---

### Post by ubu_ubu on 2007-09-07
Hello,
I've run into a similar problem as mrbig1492 above... I can sucessfully run the mkfs commands (having made sure the usb drive is unmounted) to name the drive partitions in advance of copying the Ubuntu files. But when I remove the drive and then reinsert, there is no volume name that been written to the the thumbdrive. I've tried using 'sync' before I remove the stick but still no go... What am I doing wrong? 

Thanks in advance...

---

