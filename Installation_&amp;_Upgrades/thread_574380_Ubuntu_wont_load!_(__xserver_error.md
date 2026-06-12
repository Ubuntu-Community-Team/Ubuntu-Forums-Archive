---
title: "Ubuntu wont load! :(  xserver error"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by mike29892 on 2007-10-12
Hello.  First off im a complete nub to linux and ubuntu.  I was following the guide at [http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html) on how to install beryl.  After I entered the line:
 sudo nvidia-xconfig --add-argb-glx-visuals --composite
into the console and then hit alt + ctl + backspace to restart it Ubuntu wont load.  It keeps giving me an xserver error. I tried to do dpkg-reconfigure xserver-xorg in recovery mode and It worked up until then end when it said xserver-xorg postinst warning: overwritting possibly-customised configuration file; backup in /etc/X11/xorg.conf.2007043151812 and I restart it only to get the same error again!! Thanks in advance for any help.

---

### Post by PmDematagoda on 2007-10-12
What is the error you get when attempting to initialise X? Go to Recovery Mode, then enter 

startx

If X doesn't start then press Alt+F2, or post the file Xorg.0.log using:-

```
gedit /var/log/Xorg.0.log
```

---

### Post by physguy on 2007-10-15
Mike,

I am a rookie using linux and have found myself in the exact situation that you described, when following that same guide.

To fix using

sudo dpkg-reconfigure xserver-xorg

I found that the X server video driver had changed from it's default.  I merely changed it back to what it should have been and I was able to run the window system again.

Good luck!

---

