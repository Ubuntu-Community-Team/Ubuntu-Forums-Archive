---
title: "Partitioning!"
date: 2006-03-16
forum: Installation &amp; Upgrades
---

### Post by Scottya on 2006-03-16
Hey guys.

Basically. I want to reduce the size of my HDD main partition so that I have 15gb of free space, so that in the ubuntu installation I will just select use free space. Sorted.

Does anyone know of any free partitioning software that will easily allow me to do this, or any other method.

Thanks all!

---

### Post by ninjaPants on 2006-03-16
I've used Gparted with much success. It's in the Ubuntu repos, so you should be able to get it with Synaptic. If you're editing the drive that Ubuntu's installed on, however, get the LiveCD from [here.]("http://gparted.sourceforge.net/livecd.php") 

Actually, unless you're editing a USB drive, use the LiveCD because it's a newer version and has better error handling.

[This is a pretty good howto on resizing your partition.]("http://gparted.sourceforge.net/larry/resize/resizing.htm")

HTH,
Andrew

---

### Post by Scottya on 2006-03-17
But im running windows.

I want to partition the drive for ubuntu :)

Thanks.

---

### Post by morpheus2485 on 2006-03-17
the live CD that he recommends isn't dependant upon what opperating system you use, just burn the cd, leave it in the drive and reboot.

---

### Post by Bartender on 2006-03-17
Scottya -
You have a PC with Windows installed, and you just want to make some room for Ubuntu, correct? 
I'm sure that Gparted would work for you, but it'd be simpler to just follow the directions at hermanzone

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

for doing a dual-boot.  Have you run a LiveCD to check that your PC doesn't have issues with Ubuntu?  
If you decide to do this try to get your PC set up next to another one that's displaying the hermanzone website so you can walk thru the steps.  I used the "Ubuntu+NTFS" directions rather than trying to re-format my Windows partition as FAT32.  Made a FAT32 partition so the two OS'es could hand off data.  Be advised, you may (will?) have to add a line to your fstab to get Ubuntu seeing the FAT32 partition.

Herman lists several things to do, such as backing up your data, defragging Windows, etc.  If you're going to use your own burned CD/DVD try to ensure that the download and burn went OK.  Follow Herman's "BIOS boot order" link then look for "pre-install" for more ideas.

---

