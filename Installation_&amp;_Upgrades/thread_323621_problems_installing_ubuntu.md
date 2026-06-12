---
title: "problems installing ubuntu"
date: 2006-12-22
forum: Installation &amp; Upgrades
---

### Post by scottym on 2006-12-22
I am trying to install Ubuntu on an older dell xps d266 with 64 megs of ram with windows 98. The cd will not self install. Everytime I attempt to install Ubuntu I get an error message that K-MELEON.exe will not load and is linked to missing export MRC42.DLL:6820. 

This is a new Western Digital 80 gig HDD on this machine and I tried first to install Ubuntu but could not get it to boot from the CD Rom and run from DOS so I loaded Windows 98. 

I am really disappointed I can't get Ubuntu on this machine. I have gone to Ubuntu exclusively on my laptop and it is great kicking the MS habit. I hope someone has some ideas about what to do next. Thanks.

---

### Post by raul_ on 2006-12-22
You couldn't boot from cd?

That seems like a Windows 98 error since i never saw ubuntu use .exe files. Are trying to install Ubuntu from inside Windows?

---

### Post by JayTee on 2006-12-22
your system is not booting from the CD. Check your boot options in your BIOS. I'd also recommend using the Xubuntu LiveCd or the Alternate Install CD since your hardware is older and Xubuntu is better suited for older systems with less memory.

---

### Post by djheadley on 2006-12-22
First, to install Ubuntu you will need more memory - as much as you can put in that machine.   I've not had any luch installing Ubuntu on anything with less than 128mb ram - I have 512 in my desktop. The laptop I'm running now has 188mb ram and it runs a tad slow so I'm looking for more ram for it.  Second, did you download the iso or get it from Ubuntu?  These errors sound like a bad cd.  Sometimes in downloading, you'll get a few errors.  If you can, download it again.  Also install works better on older machines if you burn the cd at 4x or less.  I usually burn at 1x just to be really sure.

---

### Post by raul_ on 2006-12-22
With 64mb of RAM i'd go with DSL

---

### Post by scottym on 2006-12-22
Thanks for the repies. The CD is the one that Ubuntu sends out and it has been working fine with my laptop. 

I am expecting some memory problems and can upgrade to 384 megs. only three slots on the motherboard, but wanted to get Ubuntu loaded first. 

The Ubuntu cd will not load. I have tried:
1/ Putting cd in and booting computer and get no operating system message.
2/ Running cd with windows and get the message state in  my first message and a really strange looking graphic.
2/ running cd from DOS which doesn't work either.

The bios is a dell flashed Phoenix BIos 4.0  release 6 which may or may not support booting with the cd since this was bought in the days of windows 95/98. i am going to reflash the bios with an upgrade from Dell.

---

### Post by NeoLithium on 2006-12-22
Do you have a liveCD or the alternate install CD?  I believe that the liveCD won't load with only 64MB of RAM; however the alternate install MIGHT; but that, think is iffy with that amount as well.  DSL Linux would be a good option if you don't want to upgrade the memory yet.

---

### Post by raul_ on 2006-12-22
Well i have the Live CD shipped by ubuntu and it says 

> 
To use the Live CD, you must have a PC with at least 256MB of RAM. To install Ubuntu, you should have at least 2GB of disk space


---

### Post by scottym on 2006-12-23
Problem loading Ubuntu is fixed! Al it took is updating the BIOS and now the Ubuntu disc will run on boot up like it is supposed to. However, It does crawl with only 64 megs of ram, I think I read that to run live Ubuntu a minimum of 128 and preferably  twice that is required.

---

