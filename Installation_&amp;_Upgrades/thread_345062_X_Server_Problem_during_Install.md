---
title: "X Server Problem during Install"
date: 2007-01-23
forum: Installation &amp; Upgrades
---

### Post by DaRush on 2007-01-23
Hey Guys,

I'm attempting to install Ubuntu 6.10 as I'm writing this.

Machine:  AMD Athlon X2 3800+, ATI Radeon X800XL 256 GDDR3 PCI-e, 20.1inch wide LG LCD (I'm using the analog conection to my monitor).  Installing on a new HD.

Installing Ubuntu 6.10 Desktop Amd64, from a Live CD. 
It boots, gives me the install menu, i Choose "start or install ubuntu," or "install in safe graphics mode" (i tried both)

After loading for a little bit, it gives me the following blue screen:
"Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?"

I choose yes, it reads among other things:
(==) using conig file: "/etc/x11/xorg/conf"
(EE) no devices detected.
Fatal server error: no screens found.

I press ok, it asks me to view the detailed report.  That reads:

(my graphics card is detected properly)
(xx) screen "default scren"

(WW) the directory "/usr/share/x11/fonts/misc" does not exist
a bunch of other warning with the same thing.

Then it gives ma a whole readout of different ATI video cards, about 10 pages long, finally ending with
(WW) ATI: PCI Mach64 in slot 2:0:0 could not be detected
(WW) ATI: PCI Mach64 in slot 2:0:1 will not be enabled because it conflicts with another non-video PCI device.
(EE) no devices detected.
Fatal Server error: no screens found.

Dinally when i press ok, it reads "The X server i now disabled.  Restart GDM when it is configured correctly."  When i press enter it just gives me a black screen.

I tried installing the same version alternate CD, that actually went through the entire installation but once i tried to restart into my newly installed ubuntu OS, it gave me the same exact screen and messages.

Now I should mention that i'm a noob to Linux and in no way know what i'm doing, but if anyone knows how I can deal with this, I would appreciate it.

---

