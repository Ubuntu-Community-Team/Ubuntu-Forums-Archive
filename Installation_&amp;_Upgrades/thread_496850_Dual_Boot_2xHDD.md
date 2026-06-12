---
title: "Dual Boot 2xHDD"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by ~X~ on 2007-07-09
Ok after reading the forum for ages I still have a couple of questions :rolleyes:

I currently have XP on a sata drive and a raw IDE drive installed, I plan to make the IDE drive the first boot and install Ubuntu 7.04 on that drive

I noticed now that 7.04 allows you to select where Grub gets installed obviously I want it installed on the IDE drive and not the sata

I know I have to use the advanced option below

[http://www.picturepile.net/files/hwnoigfmdjqng1zmf4my.png](http://www.picturepile.net/files/hwnoigfmdjqng1zmf4my.png)

My question is what exactly do I put in there is it just the drive you point it to eg (hda) or do you point it to the partition on that drive that you create ie hda1 hda2 etc

As you can see I'm a bit unclear on this part or even completely wrong ?

Also now that you can install grub where you want meaning you can install ubuntu whilst the sata drive is still connected does this mean you no longer have to edit the menu.lst


Thanks ~X~

---

### Post by ~X~ on 2007-07-10
~~ Bump ~~

---

### Post by confused57 on 2007-07-10
> **~X~ said:**
> Ok after reading the forum for ages I still have a couple of questions :rolleyes:

I currently have XP on a sata drive and a raw IDE drive installed, I plan to make the IDE drive the first boot and install Ubuntu 7.04 on that drive

I noticed now that 7.04 allows you to select where Grub gets installed obviously I want it installed on the IDE drive and not the sata

I know I have to use the advanced option below

[http://www.picturepile.net/files/hwnoigfmdjqng1zmf4my.png](http://www.picturepile.net/files/hwnoigfmdjqng1zmf4my.png)

My question is what exactly do I put in there is it just the drive you point it to eg (hda) or do you point it to the partition on that drive that you create ie hda1 hda2 etc

As you can see I'm a bit unclear on this part or even completely wrong ?

Also now that you can install grub where you want meaning you can install ubuntu whilst the sata drive is still connected does this mean you no longer have to edit the menu.lst


Thanks ~X~

To install grub to the Ubuntu drive's mbr, you'll need to type in:
```
/dev/hda
```
or however your IDE is designated by the partitioner/installer, e.g. /dev/sda

If a Window's entry isn't automatically added to your menu.lst, this thread will help:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by acelin on 2007-07-10
So, if I wanted to install grub onto the same partition as Ubuntu is on, all I do is type in the full name of that partition as it appeared on the manual partition list?

---

### Post by ~X~ on 2007-07-10
> **confused57 said:**
> To install grub to the Ubuntu drive's mbr, you'll need to type in:
```
/dev/hda
```
or however your IDE is designated by the partitioner/installer, e.g. /dev/sda

If a Window's entry isn't automatically added to your menu.lst, this thread will help:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

This is why I'm slightly confused because other guides I read said when using the advanced tab to select where the boot loader is installed you have to use the format grub uses (hd0(disk number),0(primary partition)

For example if my ext3 was on my first hard drive IDE and was the first primary partition I would put (hd0,0) as the location for boot loader ?

Already read your guide and other guides :)


~X~

---

### Post by confused57 on 2007-07-10
> **~X~ said:**
> This is why I'm slightly confused because other guides I read said when using the advanced tab to select where the boot loader is installed you have to use the format grub uses (hd0(disk number),0(primary partition)

For example if my ext3 was on my first hard drive IDE and was the first primary partition I would put (hd0,0) as the location for boot loader ?

Already read your guide and other guides :)


~X~
This is an excellent guide explaining how grub works:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

You can use either (hd0) or /dev/hda to install grub to the mbr...I personally prefer to use /dev/hda or /dev/sda, however your IDE drive is recognized by the partitioner/installer.  Installing to (hd0,0) would install grub to the root partition, which would require using another bootloader installed to the mbr...I would think you want to install grub to the mbr.

---

### Post by ~X~ on 2007-07-10
Right this is what I want to do install ubuntu 7.04 on the IDE drive including grub don't want grub on the mbr of XP thats on the sata drive

So your saying all I need to do is put /dev/hda in the advanced option box to achieve this ?


~X~

---

### Post by confused57 on 2007-07-10
> **~X~ said:**
> Right this is what I want to do install ubuntu 7.04 on the IDE drive including grub don't want grub on the mbr of XP thats on the sata drive

So your saying all I need to do is put /dev/hda in the advanced option box to achieve this ?


~X~
Yes, make a note of how the partitioner/installer designates your IDE drive...in Feisty, depending on your chipset, your IDE drive may be designated /dev/hda or possibly /dev/sda...use this designation in the Advanced option for the location to install grub to the mbr of your IDE drive.  I would also make sure your IDE drive is set to boot before your SATA drive in bios, before installing Ubuntu.

I would recommend that you burn a copy of the Super Grub Disk, before installing Ubuntu:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
SGD can boot Ubuntu or Windows and restore eithers IPL to the mbr, in case grub accidently overwrites your Window's IPL on the SATA drive, which it shouldn't...

---

### Post by ~X~ on 2007-07-10
Yeah I was going to make the IDE drive boot before the sata before I install ubuntu obviously cd rom will be first boot

Stupid question in the advanced box does /dev/hda have to be in brackets eg (/dev/hda)

I intend to do a full backup of my xp anyway in case things go wrong 


~X~

---

### Post by confused57 on 2007-07-10
> **~X~ said:**
> Yeah I was going to make the IDE drive boot before the sata before I install ubuntu obviously cd rom will be first boot

Stupid question in the advanced box does /dev/hda have to be in brackets eg (/dev/hda)

I intend to do a full backup of my xp anyway in case things go wrong 


~X~
A backup is always a great idea...no, /dev/hda doesn't have to be in brackets, only (hd0) has to be in brackets...good luck with it.

---

### Post by ~X~ on 2007-07-10
ok thanks for your help sure I'll be back :roll:


~X~

---

