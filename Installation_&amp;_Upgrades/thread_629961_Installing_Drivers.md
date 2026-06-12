---
title: "Installing Drivers"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by tedmp0816 on 2007-12-02
Hi,

After installing Ubuntu I was wondering if I have to install drivers as I do for Windows, such as chipset, video, and audio drivers.  Do I have to do any of that for Linux?  I know my sound doesn't work though, so is there any way I can check what needs to be installed.

Thanks.

---

### Post by logos34 on 2007-12-03
no, ubuntu comes with all the drivers.  Sometimes you have to change the defaults or tweak them, though (networking is the most common problem).

For video you can 

sudo dpkg-reconfigure xserver-xorg

or install the restricted driver

Sound:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

