---
title: "Serious Installation Issues"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by fuzzytic on 2007-10-12
Ok, I have tried searching the net and various forums for help topics and have even popped in and out of various IRC help channels to try and solve this - and nothing!
I'm really hoping someone here can shed some light.

Ok, in basic, I cannot seem to install a single distro of linux, be it Ubuntu or otherwise.  I had some issues in windows with my CD drive until today - which I have now fixed within that O/S, which were brought on my not having the correct IDE controller driver.
I have seemingly fixed these errors in windows, but have a suspicion that it may have something to do with the errors when trying to install linux.

The install CD will boot, bring up the menu screen, but then when I try to start the install, it will hang for quite some time on the Ubuntu loading screen, then display the following error:
*"Buffer I/O Error On Device fd0, logical Block 0"*

After the first occurence of this error, I then attempted to re-burn the CD and try again, recieving the same, I attempted to check the CD from the ubuntu boot cd menu.  The same happened, it hung for some time, and then displayed another error:
*"ata6.00: failed to set xfermode"*

I'm completely stumped!  I have never had these problems installing linux before!
I managed to get another distro to boot into their install program, after it hung while enabling SCSI drivers, only to find it would not detect any drives available to install on!

Thankyou for any help you may be able to give me!
-Fuzzy.

---

### Post by irv on 2007-10-12
I tried installing 7.10 on an older server and got some IO errors and the only way I could get it installed was to start with version 5.10 and work up to 7.10 which took some time. See my post at 
[http://ubuntuforums.org/showthread.php?t=574011](http://ubuntuforums.org/showthread.php?t=574011)
Also you never mentioned in your post what you are installing it on (spec's of your computer).
irv

---

### Post by fuzzytic on 2007-10-12
I'm running:
Motherboard: Abit AB9-pro
RAM: 3gb (2 1gb sticks, 2 512 sticks)
HDD: 2 Sata
Optical: IDE Dvd Multi
Graphics: nVidia 8800 GTS
Processor: Core2 Duo (~1.9ghz)
PSU: Tagan 700w

I have identified a potential problem that may be the source, apparently the linux kernel has some problems with a conflict between IDE optical drives and SATA hard drives?  Any more info on this?
Thanks
-Fuzzy

---

