---
title: "Uninstall Ubuntu 9.10 and reistall Vista"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by DXM31 on 2009-11-20
I did a full install of 9.10 which I like, but it won't do espn360 or use my usb tuner so, I want to uninstall 9.10 reinstall Vista(from recovery disc's) and then reinstall 9.10 dual boot.
The problem I have is I can't recover Vista from the recovery disc.
I did some searches and found I need to run /FixMbr to get rid of the Grub, and now when I put in my Vista recovery disc it just says no operating system??
I must have gotten things out of order or something.
Or maybe I can't load Vista from the recovery Disc??
Help, thanks

---

### Post by DXM31 on 2009-11-20
I think I need to do what this thread suggests 
[http://ubuntuforums.org/showthread.php?t=1260327&highlight=format+harddrive](http://ubuntuforums.org/showthread.php?t=1260327&highlight=format+harddrive)

---

### Post by darkod on 2009-11-20
Using the Vista disc ar you trying to repair or just install the system? Repair will not work because there is currently no Vista on it to repair. But clean install always works. And no need to restore the MBR in any special way if doing a clean install, the bootloader will be installed on the MBR anyway.

But if you plan to dual boot I would suggest to boot with Ubuntu CD, select Try Ubuntu option, open Gparted and delete all partitions (if that is what you want, ALL data will be LOST!!!). Then use Gparted to create just one primary ntfs partition with the size you want for your vista system partition.
Then boot with Vista DVD and install it on the already created partition. Check that it is working OK.
Then boot again with Ubuntu CD, select Install Ubuntu and install it again. When it asks where to install you can select some of the automated methods or manual partitioning, what ever you feel like doing.

---

### Post by DXM31 on 2009-11-20
I think I just managed to mess things up even more.
I now get the message "bootmgr is missing" even with the live cd
I also get it with the Vista recovery cd.
So I can't install Ubuntu or Vista

---

### Post by DXM31 on 2009-11-20
> **darkod said:**
> Using the Vista disc ar you trying to repair or just install the system? Repair will not work because there is currently no Vista on it to repair. But clean install always works. And no need to restore the MBR in any special way if doing a clean install, the bootloader will be installed on the MBR anyway.

But if you plan to dual boot I would suggest to boot with Ubuntu CD, select Try Ubuntu option, open Gparted and delete all partitions (if that is what you want, ALL data will be LOST!!!). Then use Gparted to create just one primary ntfs partition with the size you want for your vista system partition.
Then boot with Vista DVD and install it on the already created partition. Check that it is working OK.
Then boot again with Ubuntu CD, select Install Ubuntu and install it again. When it asks where to install you can select some of the automated methods or manual partitioning, what ever you feel like doing.

By the way I like you suggestion, but it maybe a little late...see above
thanks

---

### Post by darkod on 2009-11-20
But that message about bootmgr should appear only if you're trying to boot vista. If all your data is backed up and you are willing to do clean install, you are not trying to boot anything, just use the Ubuntu CD and Vista DVD as suggested.
Note: You have to select in BIOS the CD/DVD drive to be first boot device. You are doing that right? That way it will not even try to boot nor ubuntu nor vista from the hdd, it will boot from CD/DVD directly.

---

### Post by itachis.eyes on 2009-11-20
go here and download the repair console of vista: [http://www.howtogeek.com/howto/windows-vista/how-to-make-a-windows-vista-repair-disk-if-you-dont-have-one/](http://www.howtogeek.com/howto/windows-vista/how-to-make-a-windows-vista-repair-disk-if-you-dont-have-one/)

you'll endup with an ISO file which needs mounted to a disk, then boot from the disk and open up command prompt and type:
```
bootrec /fixboot
bootrec /fixmbr
exit
```now turn off the computer, and put recovery disk 1 in and start it up.

what this does is write a windows boot partition to the disk, i think thats what your asking to do. but i don't see why GRUB wouldn't be able to load the recovery disks.

---

### Post by DXM31 on 2009-11-20
the live cd gave me the bootmgr message and that kind of freaked my out.
anyway, I am reinstalling 9.1 as we speak.
I do have the iso for the vista recovery I just failed to run the other commands, I only ran fixmbr.
So my question now is, after 9.10 gets installed should I run the vista recover disc and key in all the commands this time or go with the first option?
My goal is to install 9.10 in vista so if I ever want to install a new version of Ubuntu I can just delete the old one thru Vista and install the new one.
Thanks

---

### Post by darkod on 2009-11-20
After you install Ubuntu don't run recovery for any windows. That will destroy grub2 on the MBR. That's why you need to repair windows before you start installing ubuntu, provided there is a need to repair windows.

---

### Post by DXM31 on 2009-11-20
> **darkod said:**
> After you install Ubuntu don't run recovery for any windows. That will destroy grub2 on the MBR. That's why you need to repair windows before you start installing ubuntu, provided there is a need to repair windows.

For some reason the grub2 starts with the recovery cd in without asking me to boot cd
I do have the cd in the bios set to boot first??
Either me or this laptop is getting a little wonky.
I still want vista on this machine so I will try your suggestion about loading it.

---

### Post by DXM31 on 2009-11-20
OK this is strange my computer will not boot from the cd anymore the vista recovery or the livecd, I've checked the bios a few times.
This is very confusing.

---

### Post by DXM31 on 2009-11-20
Another problem I am having is my cdrom is only working when it wants to. I am going to have to save this for another day.
Thanks

---

