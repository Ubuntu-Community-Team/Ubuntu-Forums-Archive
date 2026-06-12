---
title: "How to deal with LILO after kernel upgrade?"
date: 2006-05-15
forum: Installation &amp; Upgrades
---

### Post by jis on 2006-05-15
I just installed Ubuntu 5.10 and chose to upgrade immediately the suggested programs.  During system upgrade I got the following text (among other) and questions:

> A new kernel image has been installed, and usually that means
that some action has to be taken to make sure that the new
kernel image is used next time the machine boots. Usually,
this entails running a "bootloader" like SILO, loadlin, LILO,
ELILO, QUIK, VMELILO, ZIPL, or booting from a floppy.   (Some
boot loader, like grub, for example, do not need to be run on
each new image install, so please ignore this if you are using
such a boot loader).

A new kernel image has been installed at /boot/vmlinuz-2.6.12.10-386
(Size: 1179kB)

 Initial rootdisk image: /boot/initrd.img-2.6.12.10-386 (Size: 5164kB)

Symbolic links, unless otherwise specified, can be found in /

LILO sets up your system to boot Linux directly from your hard
disk, without the need for booting from a boot floppy.

WARNING
If you are keeping another operating system or another version
of Linux on a separate disk partition, you should not have LILO
install a boot block now. Wait until you read the LILO documentation.
That is because installing a boot block now might make the other
system un-bootable. If you only want to run this version of Linux,
go ahead and install the boot block here. If it does not work, you
can still boot this system from a boot floppy.

You already have a LILO configuration in /etc/lilo.conf
Install a boot block using the existing /etc/lilo.conf? [Yes] No
Wipe out your old LILO configuration and make a new one? [No]

I pressed enter to answer No the latter question. I guess I should run LILO before re-booting, but as I have also Windows XP Home in a separate disk partition (but in the same disk) I want to be sure to make it right. Any help on this? Can I use the live CD for recovery, if I mess up with LILO? (I do not have floppy diskette drive in the notebook I am working on.)

---

### Post by Sef on 2006-05-16
Ubuntu uses GRUB as a boot loader.  Did you install something else after or declined to install GRUB?

---

### Post by jis on 2006-05-16
I chose to use XFS file system in Ubuntu install because I think it is currently the best of the available file systems - that is why the installer did not suggest to install GRUB, but LILO. I do not know exactly what the upgrade manager meant by the LILO documentation, neither I was keen to study it. I checked /etc/lilo.conf and it seemed to be OK as far as I know and I just ran 'sudo lilo' and I guess am lucky since I am able to boot Linux and Windows (afer I found out that I have to press Ctrl during boot, if I want to load other than the default OS).

---

### Post by Sef on 2006-05-16
You can boot Grub and XFS, just you have to have a separate boot partition.

---

### Post by jis on 2006-05-16
Well I do not have a separate boot partition. Which file system should the separate boot partition have, if I had one? Wikipedia told me that GRUB prior to version 0.91 does not support XFS. Does Ubuntu Breezy use old GRUB or why does it not suggest to use GRUB? I do not see the need to switch to GRUB now and maybe it would be difficult to change partitioning. By the way, after I installed Ubuntu I read that maybe it would have been wise to have separate shared Fat32 partition that could be used by both Windows and Linux. My Windows (C) partition is in Fat32 format. Could I use that from Ubuntu? Disks Manager (ie. Sytem > Administration > Disks) sees the partition as Windows Virtual FAT and tells that the partition's status equals to "Inaccessible". However, clicking "Enable" does not change the status..

---

### Post by Sef on 2006-05-16
> My Windows (C partition is in Fat32 format. Could I use that from Ubuntu? 

Yes, you should be able to read and write from both Ubuntu and Windows onto that partition.

---

### Post by jis on 2006-05-16
I had to give "Access Path" before clicking "Enable" to make the partition "Accessible". I think I would be good, if Disks Manager would ask the access path when you click "Enable" instead of doing nothing. It seems that I can write to the partition only, if I open the File Browser from Disks Manager; otherwise the folder icon has lock in it. Could I make only some folder of the partition accessible to protect me from accidentally modifying something? (I think it would be enough, if I just could modify the contents of the "My Documents" folder.)

---

### Post by jis on 2006-05-18
The mounting of the whole Fat32 drive can be found here:
[http://users.bigpond.net.au/hermanzone/p10.htm#autofat](http://users.bigpond.net.au/hermanzone/p10.htm#autofat)

However, I still do not know how to restrict access to one folder so that I do not accidentally modify Windows files.

---

### Post by gesho on 2006-05-19
hello guys, I am trying to migrate from Mandriva 2006 to Kubuntu 5.10. Got DVD from bittorents, 3 gigs.

I've current partition:
hd2 WinXP
hd6 ext 3 
swap 2GB

I do not need anything from ext 3 (can one format just one partition, without touching the other), but I want to keep hd2 XP as is. Will installation from DVD do that? Any care needed?

My current bootloader under mandriva is LILO. Will installation take care of that too? Will I have XP/Kubuntu as new loading options?

---

