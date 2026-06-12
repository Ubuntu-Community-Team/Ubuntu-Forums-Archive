---
title: "New install, X Server won't start"
date: 2005-06-28
forum: Installation &amp; Upgrades
---

### Post by mdruskin on 2005-06-28
I get the message that X server cannot start and that I need to configure it and try again.

I think it has something to do with my video card but I am real newbie to the whole thing, so I am not sure. I tried installing drivers from the ATI website, but it didn't install (redhat only?)

Anyway, I have an ATI X800 XL, and I want to run it at 1680x1050 resolution.


Here are the log and the conf files:

[http://www.druskin.net/uploader/Xorg.0.log](http://www.druskin.net/uploader/Xorg.0.log)

[http://www.druskin.net/uploader/xorg.conf](http://www.druskin.net/uploader/xorg.conf)

Any help is appreciated, thanks.

---

### Post by mdruskin on 2005-06-28
I have installed the fglrx drivers (apt-get xorg-driver-fglrx) and still no good.

---

### Post by mingus on 2005-06-28
Take my comments with a grain of salt, there are folks hangin' out here who know a lot more than I do about X . . .

There are a lot of posts regarding that driver, I would first search the forums and google it.  I seem to recall that the fglrx is the graphics accelerator and that you should still have gotten *some* video without it.  Also saw that the X server failed to load because it did not find the expected "device" section in the conf file; note the disparity in the PCI address it was looking for vs what is in the file.

Simple thing to try:
$sudo dpkg-reconfigure xserver-xorg

Try dropping your default color depth to 16 or temporarily even 15.  Sometimes if it is too high the resolution will be dropped down.  This will also rewrite the config file, which may straighten out the other issue.

---

