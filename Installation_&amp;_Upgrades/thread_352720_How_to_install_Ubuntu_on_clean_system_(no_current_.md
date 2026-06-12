---
title: "How to install Ubuntu on clean system (no current O/S)"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by dhcook on 2007-02-03
I have just completed assembling a new system and want to install Ubuntu on it. Currently, it has no O/S installed. I attempted to boot from the image disks that I created once the machine POSTed, but I get the message - BOOT DISK FAILURE, INSERT SYSTEM DISK AND PRESS ENTER. Do I need to boot up some other way and then install from the image? I think I will do fine once I get started. Thanks!

---

### Post by taurus on 2007-02-03
How did you burn the ISO image?  Did you burn it as an ISO image instead of a data file?  If you have another system, see if you can boot from it or with a XP, insert the CD into the drive and see if you see a bunch of files and directories on the CD instead of one big file.

---

### Post by m1215 on 2007-02-03
check you bios settings and make sure your boot order is set to boot cd first then hard drive.

---

### Post by dhcook on 2007-02-03
taurus - When I view the disk in an XP machine, I only see the ISO image file on the disk - one big file. Should I have burned it in a different manner if I wanted to boot from it in a clean machine?

M1215 - I attempts to boot from the cd fine, it just doesn't like what it sees.

---

### Post by m1215 on 2007-02-03
how and what program did you use to burn the image? maybe i can tell you how to burn the image the right way if its wrong.

---

### Post by Andy_D on 2007-02-03
Looks like you have copied the image file to a cd rather than making a cd from the image file, a subtle but important difference. If the machine you burned the cd with runs Ubuntu you can simply right click on the .iso file you downloaded and select write to disk. If you are using Windows XP you will need to get some software to allow you to burn the disk image. Personally I use Nero in Windows XP but a good free alternative is ISO recorder (type iso recorder into google). Load up ISO recorder then select the .iso image you wish to burn to disk (I seem to remember the whole burning process being fairly straightforward with iso recorder), this will then make a cd from the iso image. After you have done this you can see the difference by looking at the files on the disk, instead of one large .iso file you will see multiple files. You should then be able to use this cd to install the operating system on your new hardware.

Good luck!

---

### Post by taurus on 2007-02-03
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

