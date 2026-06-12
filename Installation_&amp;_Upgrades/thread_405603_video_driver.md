---
title: "video driver"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by mr.farenheit on 2007-04-10
having slight problem with installing driver for video card, i am running an ati xpress1100 in my note book, i went to ati's site to download the driver and was unable to find a driver for linux. they only had drivers for vista and xp editions. is there somewhere else i could lok to find a driver? can i install a windows format driver in linux and if so how would i go about doing this?

---

### Post by moffa on 2007-04-10
ati does make drivers for linux.

The easiest way of installing them is installing the xorg-driver-fglrx package.  Just to let you know that it is quite common to have problems installing the ATI drivers.

If you have any difficulties, just search for the installation guide / wiki.

You can verify if it installed properly by typing glxinfo into a terminal after you restart.

---

