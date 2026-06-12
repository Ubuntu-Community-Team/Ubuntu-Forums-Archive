---
title: "[SOLVED] Loads of IO errors... tried everything (I think!)"
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by baylorbear on 2007-12-31
So I've been trying to install Ubuntu 7.10 for at least 5 hours now.  I keep getting tons of IO errors during the install.  

CD Integrity checks out fine... no errors.

I've tried reburning the image at a slower speed as has been suggested in previous forum posts... get the same errors when trying to install.

CD Drive works perfectly in Windows... no problems burning / executing any files whatsoever.

Some other points that might be of interest --

1)  Installing to a specially made partition on my second hard drive.  hda contains vista.  Attempting to install Ubuntu to hdb partition 2 (30g) with swap (4g).

2)  Not installing grub in MBR... going to follow the bcdedit approach to be safe and chainload grub.

3)  When loading Ubuntu live cd, the load screen appears for a few minutes and then jumps all over the place like there's been some sort of graphical malfunction... freezes for a few seconds, then loads on into Ubuntu without any apparent errors.  

4)  The install spits out the IO errors at random points... never at any particular install point (eg 22% 47%).

5)  If it is of any interest, Intel P4 3ghz, 1gb ram, Nvidia GForce FX 5200

---

### Post by baylorbear on 2007-12-31
UPDATE:

So it must have been my batch of CDs... because I got the install to work, BUT --- I can't boot to Ubuntu now.

I followed directions on this site: [http://www.thorsten-lux.de/files/wiki.html](http://www.thorsten-lux.de/files/wiki.html)

to which this might be my error.

My goal was to prevent the Ubuntu install from over-writing my MBR.

hda is Windows Vista all the way...
hdb partition 0 is ntfs for windows junk
hdb partition 1 is linux and the remainder is swap

When I followed the directions on the URL above -- I created the .bin file exactly as specified.

Ubuntu appears as a boot option in the Windows Boot Manager -- but all I get is a flashing cursor... no load, no hdd activity.. nothing.

I suspect that the instructions I followed didn't adequately point to Grub, but how can I change this?

When installing Ubuntu, I clicked "Advanced" just before I hit the "Install" button and changed the grub installation to hd1 from the default hd0, because it was my understanding that I had to write it to hd1 in order for the bcdedit instructions to work correctly.

What'd I do... and how do I fix it.  I'm at your mercy!

THANKS!!

---

### Post by baylorbear on 2007-12-31
Update #3:

In all of my infinite wisdom (sensing the sarcasm?) -- I decided to set the BIOS hdd boot order to specifiy my second hard drive should be loaded before the first (where grub was originally installed).

To my surprise, GRUB loaded just fine and VISTA was a load option.

Tried booting to VISTA -- got nothing but a flashing cursor... and even checked the settings and found that it correctly pointed to hd0, 0.

Tried booting to Ubuntu -- got "Error 22: Partition Not Found."

WTF?

---

### Post by confused57 on 2007-12-31
You should be able to boot Ubuntu from Vista, using EasyBCD:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

For this to work, grub needs to be installed to your Ubuntu root partition, which you can do with the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
read the instructions in this tutorial, but instead of "setup (hd0)", you would "setup (hd1,1)", or what the results of "find /boot/grub/stage1"  shows.

Added: You could also try booting first to your Ubuntu drive, make sure your first Ubuntu entry in the grub boot menu is highlighted, press "e", then select the line with root, press "e" again, change root from (hd1,1) to (hd0,1), press "enter", then "b" to boot...this is temporary if it works, but can be made permanent.

I just saw that logos34 has already helped you solve your problem in your other thread:
[http://ubuntuforums.org/showthread.php?t=654760](http://ubuntuforums.org/showthread.php?t=654760)

---

### Post by baylorbear on 2007-12-31
> **confused57 said:**
> You should be able to boot Ubuntu from Vista, using EasyBCD:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

For this to work, grub needs to be installed to your Ubuntu root partition, which you can do with the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
read the instructions in this tutorial, but instead of "setup (hd0)", you would "setup (hd1,1)", or what the results of "find /boot/grub/stage1"  shows.

Added: You could also try booting first to your Ubuntu drive, make sure your first Ubuntu entry in the grub boot menu is highlighted, press "e", then select the line with root, press "e" again, change root from (hd1,1) to (hd0,1), press "enter", then "b" to boot...this is temporary if it works, but can be made permanent.

I just saw that logos34 has already helped you solve your problem in your other thread:
[http://ubuntuforums.org/showthread.php?t=654760](http://ubuntuforums.org/showthread.php?t=654760)


Yes, and thank you for the reply! I couldn't figure out how to close this thread after starting a new one...

---

