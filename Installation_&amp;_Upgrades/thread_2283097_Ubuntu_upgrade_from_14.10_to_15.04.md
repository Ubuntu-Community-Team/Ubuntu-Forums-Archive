---
title: "Ubuntu upgrade from 14.10 to 15.04"
date: 2015-06-19
forum: Installation &amp; Upgrades
---

### Post by dschaefer79 on 2015-06-19
Hi,

I have upgraded from Ubuntu 14.10 to 15.04 and now when I launch an application, the screen goes black with every application.

Does anyone have an idea ??

Thanks,

Dominique Schaefer

---

### Post by dino99 on 2015-06-19
that issue have been often met recently on dist-upgrading. Its a graphic driver issue. Please tell us with card/chipset is used & which driver is installed

---

### Post by dschaefer79 on 2015-06-19
I have an nvidia graphic card but it's an old one. It's a Geforce 7400 G72M. I'm using the old driver nvidia-304.

---

### Post by ubfan1 on 2015-06-19
That's the correct driver, should be 304 version 125.  Did you have any special repositories like xorg-edgers enabled?  Check if you are actually running the nvidia driver (from a virtual terminal, get to one with ctrl-alt-Fn2 (function key 1-6 should work), login, and type:
 lsmod | sort
and look for nvidia or nouveau.  If you don't see nvidia, you are not running the nvidia driver.  In that case see if the driver got build successfully: with the find command:
find /lib/modules -name "*nvidia*"
you should see under your running kernel (the highest number one?, find out with  uname -a ) an nvidia-304.ko module.  if you dont see it, but only see them under your older kernels, then try to force the install again
sudo apt-get --reinstall install nvidia-current
See that the messages claim to rebuild the 304 driver, run the find command to ensure it is present, and reboot to see if video now works.

---

