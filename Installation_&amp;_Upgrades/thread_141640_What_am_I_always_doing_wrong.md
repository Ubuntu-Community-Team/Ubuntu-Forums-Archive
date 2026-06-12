---
title: "What am I always doing wrong?"
date: 2006-03-08
forum: Installation &amp; Upgrades
---

### Post by steve196 on 2006-03-08
First try to install: install program freezes after formatting the partition.
second try:unexplainedly the freeze doesn´t occur but this time the installed system misreads the partition table and finds an impossible fifth partition where there are only four.
Third try (this time with Kubuntu): After rebooting system freeze halfway into installation of remaining software. The created system has no working Xwindows (permission denied for startx) and mounting a floppy is impossible too. 
Fourth try (Kubuntu again): system installs and boots just fine. sudo is broken, but (expert this time) installation had allowed me to set a root password, so root access from console works. Admin mode in graphical apps doesn´t work (Failure to communicate with su) and starting graphical apps from the console window doesn´t work either (something like cannot contact x server). 
In all installations and in the live system dhcp fails although the network adapter (surecom ep-320x-r) is recognized.
In all installations the partition table is misread.
The computer runs perfectly well on win2k. Not a single hangup the last four years. So the hardware is not broken.

---

### Post by 11hjpphty76lkjj on 2006-03-08
You may have a bad hard drive..I've found that Ubuntu (or linux in general) is a lot more picky about the drive being in good working order.  For good reason I think.  I was having similiar problems with a laptop hard drive when I was trying to get ubuntu to boot from a usb hard drive.  I was able to install Windows great and I could format it great with windows, but everytime I tried to install ubuntu I would have all sorts of odd problems.  I replaced the drive and it worked great after that.

I know that doesn't help much..just my 2 cents..

Aaron

---

### Post by Princey on 2006-03-08
[QUOTE=steve196]First try to install: install program freezes after formatting the partition.
second try:unexplainedly the freeze doesn´t occur but this time the installed system misreads the partition table and finds an impossible fifth partition where there are only four.
Third try (this time with Kubuntu): After rebooting system freeze halfway into installation of remaining software. The created system has no working Xwindows (permission denied for startx) and mounting a floppy is impossible too. 
Fourth try (Kubuntu again): system installs and boots just fine. sudo is broken, but (expert this time) installation had allowed me to set a root password, so root access from console works. Admin mode in graphical apps doesn´t work (Failure to communicate with su) and starting graphical apps from the console window doesn´t work either (something like cannot contact x server). 
In all installations and in the live system dhcp fails although the network adapter (surecom ep-320x-r) is recognized.
In all installations the partition table is misread.
The computer runs perfectly well on win2k. Not a single hangup the last four years. So the hardware is not broken.[/QUOTE]


Assuming that the installation CD of Kubuntu is fine and the md5 check sum returns an exact match, there could be two possible culprits....

1. Your CD ROM could be faulty. From what you said, it pretty much looks so. Depending on what it feels like, some or all of the disk may be read at different intervals. I'd try using another CD ROM.
2. As kalosaurusrex said, it could be your hard drive. There's something I noticed about running Windows 2000. It reduces the fault tolerance of the drive yet Windows never reports it unless you use some 3rd party program to test it out. Linux requires a healthy hard disk to install on. It has happened to me too and changing the hard drive has yield positive results. 

Having thus said, I'd give option 1 a go first and see what happens.

---

### Post by stuporglue on 2006-03-08
I've had some problem machines like that. On some of the machiens, I can do a server install and it'll work. If the server install works, you can then log in and do "sudo apt-get install ubuntu-desktop" and all Ubuntu's GUI goodness will get installed, and hopefully work. 

I've had the problem more on low mem machines...how much RAM do you have?

---

### Post by steve196 on 2006-03-09
Thanks everyone.
I have now tried the DVD version, and it seems to work, except that there is no internet access and there is still a /dev/hda5 mounted. But those things seem to have nothing to do with the problem.

---

