---
title: "Installation Troubles"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by antonwalker on 2008-02-02
Hello,
   
    I am a HUGE Linux noob, but I am not to bad with computers. I already have vista 64bit installed and I want to dual boot.

I partitioned my drive already, to give 10gb of space to linux (Just testing it out, I am going to play with it a bit).

Ok, I set my BIOS to boot off the CD and i get to the ubuntu screen. I click on install (The first one) and it says Linux kernel is being loaded (Forgot exact words), and then my screen just goes black. My USB keyboard turns on and my old dell PS/2 keyboard turns off (???). I let it stay for about 7 minutes, but nothing else happens. My screen just stays black. 

So I am wondering if it has to do with my graphics card or what? Please help I really want to venture 
into the world of Linux.

(I don't know if this has to do with anything, but I am able to run it fine with VMware player)


Specs:
Intel Q6600
4gb 4-4-4-12 DDr2 RAM
Nvidia 8800GTX
SATA CDROM drive
ABIT IB9 Deluxe     

Thank you for reading about all my problems :)

Edit: Ubuntu 7.10 is the version, with live cd

---

### Post by jan quark on 2008-02-02
try to install via the alternate CD

[http://releases.ubuntu.com/gutsy/](http://releases.ubuntu.com/gutsy/)

here the guide
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

the alternate CD should help with this black screen which crops up often with the LIVE CD

---

### Post by antonwalker on 2008-02-02
The second link is a guide to mostly dual booting correct?


Also for the first link, is the only difference that I can't run linux off the CD without installing it on my harddrive?

I should download the 64bit alternative install cd?

---

### Post by zvacet on 2008-02-02
> Also for the first link, is the only difference that I can't run linux off the CD without installing it on my harddrive?

No that is not only difference.Read [this](http://users.bigpond.net.au/hermanzone/).

---

### Post by antonwalker on 2008-02-02
Ok, but what version should I get the x86 or x64

---

### Post by zvacet on 2008-02-03
I think that 32 bit version is good enough,and maybe better to start with.When you become more familiar with Ubuntu and if you upgrade your RAM than you can go for 64 bit.

---

### Post by antonwalker on 2008-02-03
Ok, I am now downloading x32bit alternate cd from them now. Says about 40 more minutes.

---

### Post by antonwalker on 2008-02-03
Ok....


Well I downloaded it and burned the ISO.
I got to the installation and after doing all the keyboard stuff, I get to the installation and it says it could not load the installation files from the CD. So should I redownload the whole thing or just burn it again?

---

### Post by confused57 on 2008-02-03
> **antonwalker said:**
> Ok....


Well I downloaded it and burned the ISO.
I got to the installation and after doing all the keyboard stuff, I get to the installation and it says it could not load the installation files from the CD. So should I redownload the whole thing or just burn it again?
Do a checksum of the downloaded iso:
[http://www.psychocats.net/ubuntu/iso#checksum](http://www.psychocats.net/ubuntu/iso#checksum)
compare the checksum of the iso with the md5sum from the mirror that you downloaded the iso...if they match, try burning your iso at a slower speed(8x or less).

---

