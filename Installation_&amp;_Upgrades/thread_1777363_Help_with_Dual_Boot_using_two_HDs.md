---
title: "Help with Dual Boot using two HDs"
date: 2011-06-07
forum: Installation &amp; Upgrades
---

### Post by LenWynne on 2011-06-07
On my current system I am running Ubuntu 10.10 and Win XP – each install on a separate drive. The GRUB boot menu works just as I want it to – with Ubuntu as the first selection and Win XP at the bottom (Ubuntu is on the newest drive at /dev/sdb1 and win on the old /dev/sda1) I also have a third data only HD. 

My problem is that the HD that XP is on is giving me some problems and I want to reinstall XP. Is there any way I can do this and then edit the GRUB to find the new install? I would like to avoid reinstalling Ubuntu again.

I would appreciate any suggestions and advice.

Thanks

---

### Post by wildmanne39 on 2011-06-07
> **LenWynne said:**
> On my current system I am running Ubuntu 10.10 and Win XP – each install on a separate drive. The GRUB boot menu works just as I want it to – with Ubuntu as the first selection and Win XP at the bottom (Ubuntu is on the newest drive at /dev/sdb1 and win on the old /dev/sda1) I also have a third data only HD. 

My problem is that the HD that XP is on is giving me some problems and I want to reinstall XP. Is there any way I can do this and then edit the GRUB to find the new install? I would like to avoid reinstalling Ubuntu again.

I would appreciate any suggestions and advice.

ThanksHi, yes you can,you will have to reinstall grub because xp will over write grub, you will need to boot from a livecd or usb and follow these instruction.
[http://cinderbox.net/2011/03/10/how-to-recover-grub2-after-windows-installation/](http://cinderbox.net/2011/03/10/how-to-recover-grub2-after-windows-installation/)

---

### Post by oldfred on 2011-06-07
If you have the grub2 boot loader in the MBR of the Ubuntu drive and have it set to boot first, before reinstalling windows change BIOS to boot windows first, so windows reinstalls its boot loader to sda. Then it will not overwrite grub's boot loader.

Then change BIOS back to sdb and boot Ubuntu

sudo update-grub

If you have not installed grub's boot loader to sdb do this when booted into Ubuntu:

sudo grub-install /dev/sdb

You also want to be sure grub reinstalls to sdb on updates:
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

If not the sdb drive by hard drive name:
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

