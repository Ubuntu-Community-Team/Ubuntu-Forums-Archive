---
title: "Ubutu 7.04 install broken."
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by StevOz on 2007-05-20
Specs:

Sempron64 3100+
1GB DDR400
Nvidia PCIe 6800GS 256MB
Samsung Syncmaster 713N LCD

Well that torrent finally arrived, burnt ISO, boot, tested, seems to be working....

Result....a nice little box "Not Optimum Mode, Recommended Mode 1280x1024, 60 Hz", on top of garbaged graphics, oh and then the box moves about the place after awhile, gather thats, the screensaver or such kicking in, mmmmmmm.....

Right, better try the safe graphics mode then, works a treat, except I'm stuck on a maximum res. of 1024x768, fair enough just needs the correct drivers I guess, so I'll install a dual boot and fix that later.

Dual boot all setup running fine, now for this driver issue...look into it , ah 6800GS nvidia new driver series, mmm OK, installed, nothings changed? Still stuck with the same resolution restrictions?

Right let's checkout what else, ah the monitor, mmm edit 'this' file, insert relative resolutions/scan rates save, reboot > foobar.


Yes, I didn't backup that file either, I know stupid me.

here's what happens on boot up.

> 

Failed to start X server (your graphical interface). It is likely it is not setup correctly. Would you like to view the X server output ti diagnose the problem.

<Yes>   <No>


Yes returns this......

> 

X Window System Version 7.2.0
Release Date: 22 Jan 2007
Build OS: Linux Ubuntu
Current OS: Linux stevoz-desktop 2.6.20-15-generic #2
SMP Sunday, April 15 07:36:31 UTC 2007 i686
Build Date : 04 April 2007

check [http://wiki.x.org](http://wiki.x.org) to check for latest versions

Module Loader present
Markers: (--) probed, (**) from config file, (==) Log file: "/var/log/Xorg.0.log", Time: Sun May 20 16:22:54 2007 (==) Using config file "/etc/X11/xorg.conf"


I'm stuck with a Linux Command promt, um what now?

---

### Post by enopepsoo on 2007-05-20
do you have any backup files of xorg.conf?  usually they will be xorg.conf_date.

Try editing your xorg and setting the device back to vesa, then use the restrictive drivers manager to enable your driver.

---

### Post by Ub1476 on 2007-05-20
Just open xorg.conf

```
sudo nano /etc/X11/xorg.conf
```

and delete what you added. Make it look like your previous xorg.conf:)

If you don't remember, you can always use..

```
sudo dpkg-reconfigure xserver-xorg
```

..to make a clean new xorg.conf file.

---

### Post by StevOz on 2007-05-20
Thanks for the help, yes I ended up doing exactly that tring to edit it with nano, though not being that familar with the editor and having a portion of the text missing from the lefthand side, I used the command it suggested as you suggested.

sudo dpkg-reconfigure xserver-xorg

This worked, selected Nvidia and my resolution and it's now working again, but someting still is not right, it flashed up something about display issues. I'm still stuck at 1024x768 @ 50Hz.

Now how do I fix this? My recommended and prefrered monitor resolution is 1280x1024 @ 60Hz.

---

### Post by zvacet on 2007-05-20
[https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto")

---

### Post by StevOz on 2007-05-21
Thank zvacet,

Almost got it sorted, got 1280x1024@54Hz so far...getting close

Added modeline calculated using my specs here...

[http://www.samsung.com/in/products/monitors/tftlcdmonitors/713n.asp?page=Specifications](http://www.samsung.com/in/products/monitors/tftlcdmonitors/713n.asp?page=Specifications)

and this online modeline calculator.

[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

edited config file, added modeline, changed H sync and V sync to specs and added 1280x1024 to all those resolution settings.

Still not right yet, I want my 60Hz, have an option for 55Hz, but that does not fill the screen and it's still not 60, 54Hz is still a little blurry.

---

