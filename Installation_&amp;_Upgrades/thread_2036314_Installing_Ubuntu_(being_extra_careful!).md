---
title: "Installing Ubuntu (being extra careful!)"
date: 2012-08-01
forum: Installation &amp; Upgrades
---

### Post by *^kyfds( on 2012-08-01
Due to the fact that i accidentally corrupted the windows partition on the only other  machine i've installed ubuntu on, i'm not entirely willing to be brave and go ahead with installing it on my nice shiny netbook without seeking some advice first.

Anyway, the laptop i want to install this already has a windows 7 OEM installation( with which i want to dual boot), and a recovery partition (which i don't know the size of).

I want to be able to return the laptop to it's (almost) factory condition if i have any serious problems with ubuntu, or my hardware packing up (boot loader, partitions ect.).

will i be able to install ubuntu onto my laptop without replacing the windows boot loader with grub, so that i easily just erase the partition and edit the windows boot loader to return it to how it was?

please point out any mistakes i make, as i'm still quite new to ubuntu. as well as complex boot systems.

---

### Post by darkod on 2012-08-01
It's much easier to allow grub2 to be the main bootloader. Whether it deletes the windows bootloader from the MBR or not makes no difference.

Just in case, make a set of recovery DVDs (the recovery software should allow that) and that way you have a bootable set of DVDs you can use even if it can't boot from the hdd at all.

Not sure how you corrupted the windows partition on the other machine, but if you installed using the Install Along Side... option and used the slider to split the disk between them, DO NOT do that. First in windows open Disk Management and shrink the win7 partition that way. Leave the newly created space as unallocated, don't create any partition from it.
The ubuntu installer will use that unallocated space not touching the win7 partition.

Disk Management will also show you the total number of partitions because some of them are hidden in windows. If you have 4 primary partitions you have to delete one at least because ubuntu can't create its partitions. The limit is 4 partitions. In that case you have to decide which partition to delete, one idea is to delete the recovery partitions once you have created the recovery DVDs.

---

### Post by *^kyfds( on 2012-08-01
i don't think the recovery software has the option to create any recovery CD's.

besides, this netbook has no CD drive, i'm planning to install ubuntu by usb.

---

### Post by *^kyfds( on 2012-08-01
oh, and the partition on my old machine was currupted when i tried to format it, just before a power surge.

all of my electronics reset, including my PC, and the partition would not format ( i had to replace the hard drive)

---

### Post by oldfred on 2012-08-01
+1 on Darko's comments.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

You can easily restore the Windows boot loader if you have a Windows repairCD/USB or a boot loader that boots Windows with Boot_repair

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by *^kyfds( on 2012-08-02
thanks for the prompt reply.

i've started backing up my computer with the macrium software you mentioned, although i won't be able to download the Ubuntu ISO yet because i'll have no internet for the next three weeks 

:popcorn:

---

