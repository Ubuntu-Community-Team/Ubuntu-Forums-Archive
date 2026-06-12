---
title: "[SOLVED] restricted driver causes blue haze over an offset desktop area"
date: 2008-06-29
forum: Installation &amp; Upgrades
---

### Post by misterhead on 2008-06-29
This is weird. I installed Hardy on a Frankenstein machine consisting of a motherboard from a HP Media Center Edition Desktop. One of the first ones made. 2001 2002 something like that. First installation was with a Nvidia G-Force 2. Once I enabled the restricted driver, my sign on screen would offset way to the right and slightly up, and have a strange blue haze over it. I thought it was just because of the older video card. I reinstalled with my Radeon 9800 Pro in it and the same thing happens after enabling the restricted driver. The same thing happens with the desktop environment as well. Could this be related to the Bios perhaps. It still splashes the old blue HP screen at startup. Maybee I can get a new bios for this board specifically without it being from HP? Is that even the issue? Ultimately I would like to keep the 9800 Pro in here for every reason in the book, but I want to be able to use it to it's full potential. Any help with the bios or with the 9800 pro and Hardy combo would be great.

---

### Post by dstew on 2008-06-29
It is probably an issue with the restricted driver, not your BIOS. Try to re-configure your display (get rid of the restricted driver) by booting in Recovery Mode, and chosing **xfix** from the Recovery Menu. That should get you a basic desktop. Once you have a desktop (before you try to install a restricted driver) hit alt-F2 to get a command line, and enter```
gksudo displayconfig-gtk
```That gets you a graphical tool to set up the display. Try to find your exact monitor type.

If after you re-configure your display you are satisfied, I would recommend not trying to install the restricted driver. I have a fairly old Dell with a Radeon X300, and the restricted driver really blows it up. I don't get desktop effects with the regular Ubuntu driver, but the desktop is perfectly useable.

---

### Post by misterhead on 2008-06-30
Thanks. I was able to get back to the normal driver and compiz works fine from what I've tried so far, but I can't use a 3d effects screensaver (Euphoria) and that sucks. I'll keep dink'in with it.

---

### Post by misterhead on 2008-06-30
Update...
Screen saver DOES work SOMETIMES. Seems like every other time or so. (weird) Even tried the newest Catalist driver that got things working great on my laptop (thanks to another thread that I'm subscribed to), but had the same blue offset issue with this desktop. But as it stands, I still have Compiz and sometimes gl screensavers with the standard Ubuntu driver on this 9800 pro. Better off leaving well enough alone? Still wondering if the bios might have something to do with it. (not to mention I would LOVE to get rid of that HP splash screen!)

---

### Post by markbuntu on 2008-06-30
That may be an oem board. HP used ASUS oem boards for a lot of their media center pcs.

If so ASUS does/will not support it and you need to get an updated bios from hp which I am sure they have and you need. It's pretty painless to get. Their web site is fairly well organized for pc info/support as long as you know the correct model.

---

