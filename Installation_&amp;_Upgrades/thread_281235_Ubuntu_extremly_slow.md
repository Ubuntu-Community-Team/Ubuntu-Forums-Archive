---
title: "Ubuntu extremly slow"
date: 2006-10-20
forum: Installation &amp; Upgrades
---

### Post by onkelsatan on 2006-10-20
Hallo,
So, i have just installed ubuntu on my laptop which went very smooth. However after rebooting the system things started to get a little sour.
First when booted up via. the cd the system was wroking very well but now that the system is installed on the harddrive the system is increadebly slow. First off the bootup takes ages, but most worring is that all application takes way WAY too long to startup. As an example the terminal takes around 15-20 sec. to start up. The same goes for every other application.

Any idea to what is cousing this ?

My system is:
Celeron 2.5 GH
1 GB ram
intel 82845 graphic controller (yes i have the 640x480 problem aswell)

Apart from that everything seems to be working, usb devices, wireless network etc.

What i find really strange is that the system operated really well after booting with the cd but now it all sucks :(

---

### Post by madmetal on 2006-10-20
open a terminal and run
sudo hdparm /dev/hdc 
to see if dma is on..
about graphics do you have the driver installed?
run  glxinfo | grep direct to see if 3d acceleration is on.
about boot up speed i think 6.10 is way faster so give a try..

---

### Post by onkelsatan on 2006-10-20
/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

im currently running 6.06
How do i update to 6.10 ? (new to the hole linux thing)
Btw. i got the resolution fixed. Need to add the horizontal and vertical sync/refresh rates.

---

### Post by madmetal on 2006-10-20
look here for upgrade 
[https://wiki.ubuntu.com/EdgyReleaseNotes](https://wiki.ubuntu.com/EdgyReleaseNotes)
We consider this release candidate to be complete, stable and suitable for testing by any user.
The final release of version 6.10 is scheduled for 26 October 2006 and will be supported for 18 months on both desktops and servers. Note that the current stable release (6.06 LTS) is a long-term support release, and so users requiring a longer support lifetime may choose to continue using that version rather than upgrade to 6.10. 

but i think edgy is faster so if you have a problem with slow speed give it a try..:-k ;)

---

### Post by onkelsatan on 2006-10-20
okey then ill give it a spin, hopefully it will solve my problems.

---

