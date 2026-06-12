---
title: "Need help with grub recover command."
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by wizarddrummer on 2010-07-27
Hello,

I just upgraded to Ubuntu 10.04 LTS and installed all upgrades (including grub)about a week ago. Love the upgrade, went smooth as silk.

However I do have a small problem that I hope someone can help me with.

I have computer with limited 430W supply.

The computer has:
2 -  SATA power connector, 
1 - 4 pin Floppy Drive connector, 
3  - standard 4 pin power connectors, (1 is used for the video card) leaving 2 for hard drives. 

Computer:
250 GB hard drive with Ubuntu. (4 pin)
41 GB hard drive with Windows XP installed. (4 pin)
SONY DVD Writer (4 pin)
500 GB SATA hard drive (SATA)

I do not have any cables to convert SATA to 4 pin and there is no store available purchase this item. I am not in the USA.

As you can see, when I need to use the DVD I have to unplug a hard drive.

When the 250GB and 41GB hard drives are connected grub gives me an option for booting to Ubuntu or XP. This works great.

But, in this case, I need to boot from the XP drive and use the DVD which means I have to unplug the Ubuntu drive.

The problem is when I unplug the Ubuntu drive and change the BIOS to boot from the 41 GB XP drive, XP will not boot normally. I get a grub recovery prompt. I have no idea why it would do that when only the XP disk is turned on. I suppose grub installed some information on that drive.

What do I need put at the grub command line to allow it to continue on and boot XP normally? 

Thank you.

---

### Post by confused57 on 2010-07-28
With the Ubuntu drive unplugged, you could boot up a Window's installation cd(a restore disk won't work), press R, then enter "fixmbr"(without quotes).

If you don't have a Window's install cd, you could boot an Ubuntu live cd, and in a terminal:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Ignore any warnings you may get(you're not actually installing lilo, but just it's boot to the mbr).
You might first want to run:
```
sudo fdisk -l
```
-l is a small "L", to determine if your Window's drive is /dev/sda.  Make sure not to type a number(e.g. /dev/sda1), after sda.

---

### Post by wizarddrummer on 2010-07-28
> **confused57 said:**
> With the Ubuntu drive unplugged, you could boot up a Window's installation cd(a restore disk won't work), press R, then enter "fixmbr"(without quotes).

If you don't have a Window's install cd, you could boot an Ubuntu live cd, and in a terminal:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Ignore any warnings you may get(you're not actually installing lilo, but just it's boot to the mbr).
You might first want to run:
```
sudo fdisk -l
```
-l is a small "L", to determine if your Window's drive is /dev/sda.  Make sure not to type a number(e.g. /dev/sda1), after sda.
Thanks

---

