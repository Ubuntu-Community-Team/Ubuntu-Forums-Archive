---
title: "Outline for Live USB (on a flash stick)"
date: 2005-11-01
forum: Installation &amp; Upgrades
---

### Post by DaBruGo on 2005-11-01
Hi Folks,

I did a google search on some words (make live cd usb) and found some info on a Gentoo Linux site that may work for this, but I need your help to fill in this outline. Here are the basic steps given (which I believe were run from within linux) to get a Live CD onto a USB Flash Stick ...


(1) write an MBR to the USB memory stick (using a dd command)

(2) format the stick with vfat (which i think is good ole FAT, or FAT16)

(3) mount the stick (using a mkdir command and a mount command)

(4) copy the live cd contents to the usb stick (using the cp command)

(5) unmount the stick (with the umount command)

(6) run syslinux on the stick to make it bootable


Supposedly that's all we need to do. Can some of you "guru guys" fill out this outline with the meaty details. I can test it out on my USB flash stick (1GB in size) to see if it really works.

Just imagine it ... Ubuntu on a memory stick!

That would rock! And on a 1GB flash stick , there would be room for another partition to store our files on!


Whose up for the challenge?
DAVE

---

### Post by megamania on 2005-12-27
Just found this old message - I searched for this topic since I was going to try the same thing: I'm a happy Ubuntu user, but I'd like to check the kubuntu live cd. I have no cd writer at the moment (doesn't work anymore), so I'd like to use my 512mb memory stick...

Did you manage to do it? Would it fit on 512mb?

Does anybody else out there know how to do it, or point me to some specific link / howto ?

---

