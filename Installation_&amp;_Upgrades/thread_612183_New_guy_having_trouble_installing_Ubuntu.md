---
title: "New guy having trouble installing Ubuntu"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by Miles_Militis on 2007-11-13
Hello, (my apologies if this is in the wrong forum)

As a Windows guy by nature (*waits for bashing*), I've decided its time to dip my toe in the Linux waters by running Ubuntu on my laptop (live CD).  Unfortunately however, I can't seem to get it to run.  A guy in one of my computers classes said it was probably my nVidia video card, and that there have been issues with nVidia in the past.  I've done a little searching, but I can't seem to find instructions on how to get around this.  I'm completely new to anything but Windows so be gentile.

My problem is just after what looks like a progress bar 'pong style', when it goes through some text.  It just seems to freeze up with a blank screen.


My laptop Specs (an HP Pavilion dv6000):

AMD Turion 64 X2 Mobile Technology TL-56 1.8GHz
2GB RAM
nVidia GeForce Go 6150 (with something like 64MB RAM)


I apologize if this has been posted before, I've done some searching but I could have missed something.  Any help would be greatly appreciated!

P.S.
When the 64bit AMD version of the CD didn't run, I downloaded the regular i386 ISO, but that couldn't get past the main menu.  Oh, and I'm trying to install Ubuntu 7.10.

---

### Post by torgrot on 2007-11-13
See the sticky at the top of this forum about HP Laptops.  It doesn't look good for running Ubuntu on your laptop.

torgrot

---

### Post by Miles_Militis on 2007-11-13
I saw that, but wasn't sure what gutsy / feisty / edgy was.  Are they different versions of Ubuntu?  I'll just hold off on Linux then.  I'll give it a shot when I get a new desktop.  Thanks!

---

### Post by torgrot on 2007-11-13
Yes,  Gutsy is the latest, then Feisty and finally Edgy is the oldest.

torgot

---

### Post by lonniehenry on 2007-11-13
Miles_Militis don't give up easily.  Gutsy should run on your machine.  There are several threads about running on a hp 6000,  You will note that early in the threads the problems were hard to solve. As Ubuntu evolved it has gotten easier.    Start with a new download of the iso for AMD64 and then burn it slowly.  That seems to keep errors from occuring in the cd. Try some of the hints about booting with noapic and noirqdebug. The nvidia card will install with the restricted drivers manager and wireless may not be too hard either. Use the search feature in the forums to find solutions to problems as they occur.
Good luck 

--------------------------------------------------------------------
amd turion 64x2 tl-50, broadcom 4311, nvidia geforce 6150, 1 gig, 80 gid hd

---

### Post by tubasoldier on 2007-11-13
I used to have an HP laptop. Your going to be fighting an uphill battle. it has nothing to do with Nvidia and everything to do with HP.

You may not be able to get Ubuntu to run, However, I was able to get Mandriva to run on an HP 6000. Also, I'm not sure if they have fixed this, it used to be that HP had a crappy bios for their dual core systems. it would return a temperature of 0 degrees celcius. Linux, seeing a temperature of 0 degrees must think something is wrong, so it shut off. That may be what is happening here. I called and complained but of course it was my software that was the issue, not their junky BIOS. Thus I no longer own said laptop.

---

