---
title: "video hiccups - using ext USB drive on multiple PCs"
date: 2005-10-24
forum: Installation &amp; Upgrades
---

### Post by DaBruGo on 2005-10-24
Hello,

I have successfully loaded Breezy (using the INSTALL CD) at home on an external USB hard drive that has an ATI Radeon video card in it. 

When I brought the external drive to work and connected it to my work PC (Dell Optiplex with embedded video), I got the dreaded error message that X server couldn't start.

But, when I tried using a LIVE CD on my work PC, Ubuntu loaded just fine.
 
I was wondering if there is a way to add multiple devices and monitors to the xorg.conf file so that it can intelligently pick the correct device/monitor ... OR ... is there another way to have Breezy automatically detect my device/monitor and load the correct drivers - just like the LIVE CD does.

I have seen other posts where you can add the vga=771 (for 800x600 mode) to the end of the kernel line in grub ... which has fixed some people's video headaches. (I tried using the vga=773 parameter option with the LIVE CD on my work PC and it worked fine ... loading Ubuntu up at 1024x768.)

Would this also fix my video problems, if I added this line to the grub menu.lst file on my external USB hard drive?

There has to be a way to do this because I have seen a few flash-type drives out there on the web that are able to be connected to almost any PC and work just fine on the video side. The linux version loaded on these drives must have a way of knowing which video card and monitor drivers to load. I would like to have this same functionality on my external USB hard drive.

Anybody got any suggestions on this?


DAVE

---

### Post by leezer3 on 2005-10-24
Hiya, probably the best way to do this is to use the driver vesa in your Xorg.conf- This is a totally generic driver with no 3d acceleration etc, but which will still give you a decent working desktop.


Hope this helps.

-Leezer-

---

