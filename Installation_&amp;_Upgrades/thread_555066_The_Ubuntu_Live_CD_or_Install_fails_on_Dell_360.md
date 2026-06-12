---
title: "The Ubuntu Live CD or Install fails on Dell 360"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by Proximo1 on 2007-09-19
Hello Linux Community,

This is my first thread and I would like to mention that I tried my best to search for my problem and come up with nothing, or at least I did not see any threads that covered the failure I am having.

I have been using Windows since 3.11

The reason I started to learn Linux was due to a software analysis program we are looking at purchasing.  The recommendation to us from the company was to run it on Linux.

I installed Linux on VMWare successfully and quickly fell in love.  I consider myself an advanced Windows User but never gave Linux a try until now.

First I want to say that I love and respect the Open Source Community and I love learning new things.  Linux has gotten me more excited than anything I can remember in a long time.  I think part of it has to do with the Open Possibilities I see within the community.

Now I am ready to install Linux on a system as the only OS.  No dual boot, no VMWare.  This system is a Dell Precision 360 Workstation.  I can boot from the Ubuntu CD and I have version 7.04 I believe.  When I choose to run or install Ubuntu, the computer locks up with an error.  I am not able to run the Live CD version and choose the Install icon like I did when I used VMWare.  

This is a different system that I am trying to install Ubuntu on.

The specifications of this system follow:

Dell Precision 360 Workstation
CPU: Pentium 4 2.40 Ghz
Chipset: Intel i875P
512 L2 Cache
800 Mhz Bus
1024 Megabytes of RAM: (4 x 256 MB DIMM's)
80 Gig. Hard Drive
Nvidia Quadro FX 500 Display Adapter with 128 MB RAM.
SoundMAX Integrated Digitial Audio
Samsung CD-ROM SC-148C
TDK CDRW5200B CD Writer

I get the same error screen when checking the CD for Errors as I do when I try to run the Live CD.

This same CD works when I install Ubuntu on my VMWare so I figured the files where all available and present.

Here is the error I get once the Ubuntu Progress Bar shows up.  After about 15 seconds, I get the following.

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs) [ 59.627519] ata2.01: failed to set xfermode (err_mask=0x4)

The next 3 lines are similar to the second with the numbers in [number] changing.

I have no idea what to do now.  At least this screen has more information than the Blue Screen of Death.  :-)

Any help or suggestions would be greatly appreciated.  I am so fired up about learning Linux and becoming part of this community.  Thank you in advance.

---

### Post by Proximo1 on 2007-09-19
Although I did not receive any help on this,  I do want to mention that I am going to try the alternative CD install using text. 

I am downloading it now.  Hope it works.

---

### Post by Pumalite on 2007-09-19
Excellent idea. Hope it works for you.

---

### Post by confused57 on 2007-09-20
Maybe this will help:
[http://fak3r.com/2007/06/22/failed-to-set-xfermode-solved/](http://fak3r.com/2007/06/22/failed-to-set-xfermode-solved/)

You could try booting the live cd, press "F6", then add irqpoll to the boot parameters on the kernel line.

---

### Post by Danikar on 2007-09-20
I am having the same problem and that didn't work for me =\.

Tell me if the alternate works for you.

---

### Post by 0darn on 2007-09-20
- it could be the "Samsung CD-ROM SC-148C" , usually it result in "cant access file" or simular on boot from a Live-Cd, try with another spare CD-ROM if you have ?
/ good_luck - 0darn

( if this true - theres maybe time for a firmware update on the Samsung ? )

---

### Post by Proximo1 on 2007-09-21
I tried the text based install CD and it worked.

I then tried to install the latest Nvidia drivers and my Kernel got messed up.  I decided to re-install Ubuntu and now it won't install.  It said it has an error installing the Kernel.

Does the Installation process completely wipe out the Hard Drive?  I would think it would, but it seems to look at my corrupt Kernel anyway.

What do I do now?

---

### Post by Pumalite on 2007-09-21
Get Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
Delete all partitions in your hard drive (if you have something to save, do it ahead of time), then make one large partition of your hard drive, format to ext3 if you want, then install again. This time come back for advise on your drivers.

---

