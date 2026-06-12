---
title: "can't install Ubuntu"
date: 2005-09-10
forum: Installation &amp; Upgrades
---

### Post by frefel on 2005-09-10
I received my Ubuntu installation CDs and wanted to install Linux in place of Win2K that I have on an older Dell laptop that I believe has adequate specs for this Linux OS. I put the install CD in the drive and rebooted the computer, the drive spins and sounds like it is doing something useful but Win2K just goes on loading with no hint that the computer is reading the CD. I enabled the Boot Logging but there is no other OS listed except Win.  I've never before seen such a stable Win. platform now that I want to delete it. How can I get rid of Win. and replace it with Linux?
Thanks in advance.

---

### Post by rafakl on 2005-09-10
Check in the BIOS settings of your computer to boot from the CD not the HD. It doesnt matter if it sounds and spins... if your computer is not configured to boot from the CD then it will start from the hard disk.

---

### Post by lig on 2005-09-10
goto [http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm) download a windows 98 boot disk and get a disk then run the program then when its done putting the file into the disk reboot your machine then when it gets to command line or dos type _format C:_ doing this will wipe your hard drive after wiping your drive install ubuntu format

---

### Post by rafakl on 2005-09-10
I think he dont need to do that, because the problem is that he cant boot from the cd.

---

### Post by blueturtl on 2005-09-10
> I put the install CD in the drive and rebooted the computer, the drive spins and sounds like it is doing something useful but Win2K just goes on loading with no hint that the computer is reading the CD.

Your computer is set to boot from hard-disk first.
Find out which model your laptop is, then search for the key-combo which on your computer let's you access BIOS. On most computers it's either Del or F1, but laptops are known to sometimes have more bizarre BIOS intro keys. Anyway, once you find out which key you need to press, reboot the computer and hit the key before reaching the Windows boot screen. Then, from BIOS change the boot order so that CD-ROM will be the primary boot option. You may want to change this back after you have installed Ubuntu.

---

