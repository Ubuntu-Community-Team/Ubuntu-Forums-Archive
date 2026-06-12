---
title: "HELP! Corrupt CD Issues"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by rmstone1s on 2008-05-05
I need help... i've burned probably 15 8.04 ubuntu CDs, all corrupt...

I've checked my downloaded files, the md5sum on them is fine... i've tried two different PC to do the burn on, so two different burners... i've tried max speed, slow speed, medium speeds (including a speed of 1).  I even went out and bought SONY CD-Rs thinking my maxell's were the problem.  I also tried different files from different mirrors (i'm trying the 8.04 alternate 32-bit).  I've tried ISORecorder V2, PowerISO, and Power2GO

At this point I'm lost... i've burned 7.04 in the past and usually get 1-2 bad discs before I get a good one... but I cannot get a single 8.04 to work.

Does anyone have anymore ideas?  This is very frustrating... i'm baffled as to what could be doing this...

---

### Post by djohnston on 2008-05-05
I believe I am having the same problems.  Any help would be greatly appreciated.

-David

---

### Post by pro003 on 2008-05-05
It seems like your cd/dvd-rom you're using is gone for good or maybe needs cleaning... did you try to burn that image at your friends computer? i have downloaded x32 i386 alternate iso image of ubuntu 8.04 and burned it with max speed and got it workig at once...am just proposing...

---

### Post by rmstone1s on 2008-05-05
Tried two sets of brand new CDs and two different computers... burned on both my work dell and my home hp laptop... nothings working.

I did get the live CD to burn successfully somehow, but it won't boot properly (doesnt like my video card i think).  thats why i've always opted to use the alternative CDs.

-Randy

---

### Post by Pumalite on 2008-05-05
It seems the time to sink your teeth in some boot parameters:
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off vga=0x317 vga=791

---

### Post by rmstone1s on 2008-05-05
Are you recommending i use boot parameters on the live CD?  If so where do I put those parameters?  Is there a temporary way to apply them for a live CD boot?

I'd much rather have a nice working alternative CD.

---

### Post by Pumalite on 2008-05-05
You might need boot parameters even with the Alternate CD. There are several How-To's linked.

---

### Post by RJARRRPCGP on 2008-05-05
> **rmstone1s said:**
> 

I did get the live CD to burn successfully somehow, but it won't boot properly (doesnt like my video card i think).  thats why i've always opted to use the alternative CDs.

-Randy

You don't require the alternate version for new video cards, unless the version you're using don't have support.

Warning, Dapper Drake apparently don't support GeForce 7600s! 
You probably will get a black screen! 

GeForce 7600s apparently require at least Edgy Eft, if not at least Feisty Fawn!

---

### Post by rmstone1s on 2008-05-05
The live CD has never worked for me in ubuntu... i've had to use the alternate and then tweak some settings before it would boot.

And currently the live CD goes to a black screen when i choose to install.

---

### Post by lemming465 on 2008-05-05
When you say the CD's are corrupt, do you mean they don't read back with same MD5 sum as the ISO image, that they fail their self-test, or that they don't work?

The first is common if the CD burning applications pads the ISO with some extra blank sectors when it burns it.  The second indicates it's actually corrupt.  The third is what you are after, obviously.

Do your CD burners burn other non-ubuntu disks successfully, e.g. a Fedora 9 beta?  Can they read other disks, e.g. an older existing Ubuntu 7.10 or 7.04 disk?  Have you tried running a cleaning disk through them?

Also, try running memtest on the computers you are doing the burning from.  Burning a CD stresses the memory, and if some of that is bad, you are never going to succeed until that is fixed.

---

### Post by Pumalite on 2008-05-05
While you are at it; check all your cables and connections.

---

### Post by rmstone1s on 2008-05-05
Solved guys...

Checked the CD for defects on another PC and it said it was good.  Turns out I have 15 valid Ubuntu disks and a dirty CD drive... gave the the drive a run of my cleaning disk and blew into it real hard and now its installing fine and saying the disks are valid.

Thanks!

---

### Post by rmstone1s on 2008-05-05
Take that back... it agrees my CDs are valid, but still failing at the select and install software section.  If i skip to the GRUB or LILO steps those fail also.

---

### Post by Pumalite on 2008-05-05
Try your CD's in a different computer.

---

### Post by kajer on 2008-05-05
I have had the same issue with the 8.04 Server disc...

I have duplicated this issue on these machines...

 dell poweredge 2450
 ibm netfinity 5100
 ibm netfinity 5500
 my amd desktop
 vmware
 my intel(chipset) laptop

[IMG]http://www.czarkahan.net/kajer/bad804serverdisc.png[/IMG]

funny thing was, when I mounted the ISO file for vmware to use, it checked the CD and everything was perfect. When I used a burned CD, it failed the check.

I have used 3 different burners to make the 8.04 server disc, one of which was out of the box NEW!

What's going on here?

---

### Post by lemming465 on 2008-05-08
If vmware likes the ISO image, but 5 different computer hate the burned CD, and different burners aren't helping, I'd try different media.  Or switch to an installation method that doesn't involve using a physical CD.

* install from network
* install from USB
* install from ISO image

See e.g. [Feisty boot alternatives]("https://help.ubuntu.com/7.10/installation-guide/i386/howto-getting-images.html") for some ideas.

---

### Post by Pumalite on 2008-05-08
This might help:
[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by derby007 on 2008-05-09
I downloaded the new 8.04 (Alternate CD) and I got a similar problem last nite, it fails at Install Software section !!!
My download mirror was the 'heanet.ie' site. 
Note: I've never had a problem with previous versions of Ubuntu.

---

### Post by pro003 on 2008-05-09
yesterday happened to me too while installing 8.04 on my friend's desktop... the same cd i was using on my desktop and didn;t have any problem at all... strange, i don't know does it matters on which hardware you use it (cd)?:confused:

---

### Post by Pumalite on 2008-05-09
The Servers are not working well.

---

### Post by pro003 on 2008-05-11
not in my case... i have downloaded .iso file and never had a problem with 2 different desktops and one laptop... something else is causing my problem cause this desktop on which i couldn't perform installation is way different from my two desktop and the laptop i've mentioned... it has integrated wifi (onboard) and graphics... that's not maybe it but i'm just guessing that might be a problem... as far for corrupted cd - that's whole different story...

---

### Post by julianop on 2008-05-11
I've just spent a day trying to burn a good 8.04 disk too. I'd been using Office Max disks and kept getting bad MD5 checks - on /casper/initrd.gz.
I burned an Acer disk and I'm now up and loading.
It is interesting that I'd got a successful burn/install on an Office Max disk the other day when I installed on my Dell Inspiron 9200 laptop, but the same disk wouldn't work on my older Gateway Solo 5350 laptop.
It doesn't seem logical to me that a particular distro would be fussy on media, but several posters to this thread - and I - seem to have experienced just that.
Maybe it's the pad bytes or something.

---

### Post by kajer on 2008-05-11
I made some headway last night. I used a plextor external dvd/cd writer and booted a 8.04 server cd from the USB drive.The defect test came out flawless, however, i tried to use a phillips dvd/cd writer to bot the disc on my laptop, no luck.

This helps and doesn't help.

I want to install server 8.04 on my netfinity 5100 server, which doesn't support usb boot devices. I had to run a 8.04 server disc in expert mode, and just before i selected the option to find and mount cdrom, i pulled the 8.04 server disc out of the servers dvd drive, and put it in the plextor usb drive.

The installer looked at the usb device, found the ubuntu cd, and proceeded with no errors... just had a problem trying to so some software raid...but thats a different issue.

So basically I think it might have something to do with the cdrom drives chipset, but I cant be sure...All I know is ubuntu needs to be re-packed so the iso will work in ALL drives, new and old.



edit: when i get home, I am going to repack the ISO myself and see if this does anything... I'll post my results here

---

### Post by pur@evilcom on 2009-03-06
Almost a year I wonder if the repack worked?

---

