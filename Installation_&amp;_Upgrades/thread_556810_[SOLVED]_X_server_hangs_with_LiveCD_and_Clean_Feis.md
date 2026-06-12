---
title: "[SOLVED] X server hangs with LiveCD and Clean Feisty Install"
date: 2007-09-21
forum: Installation &amp; Upgrades
---

### Post by nowhere@cox.net on 2007-09-21
Hi everyone,

When I boot from the LiveCD and choose the first menu item, when the Ubuntu logo pops up (I assume this is when the x-server is initialized), the screen is somewhat garbled and then the system hangs totally. If I use safe graphics mode it works find and I can install but when I boot to the new install, x-server starts and the same thing happens.  It's an amd64 system, with an nvidia 7800 GT card. 

I tried the dpkg-reconfigure but it did not change anything. I had a similar issue on a totally different machine with a totally different nvidia card. There I was able to load the restricted drivers which fixed the problem. 

This current install the system hangs before I can do anything. Any ideas why the 'nv' driver is having trouble? How can I install the restricted drivers from the recovery boot?

If needed I will boot the LiveCD in safe graphics mode, mount the linux partition to get the xorg.conf and log files.

Thanks!
Eric

---

### Post by Pumalite on 2007-09-21
sudo nvidia-glx, or
sudo nvidia-glx-new

---

### Post by dabl on 2007-09-21
Start it in text mode.  Log in, and then do this: 


```
sudo dpkg-reconfigure xserver-xorg
```

This starts the X server configuration script. On the first screen, answer "NO" to the autodetect question (because we already know what happens when it tries ....), and on the second screen choose "VESA" as your display type.  Then you can accept the defaults until you get to the "monitor" section. On that screen, put an "x" only in one resolution that you can comfortably use, like 1024 x 768, or if it is a small display maybe 800 x 600.  Then enter refresh rates appropriate for your LCD or CRT monitor.  When completed, it will dump you back to the text prompt. At that point you can enter

```
startx 
```

and you should get a reasonable GUI, in which to continue your excellent adventure.

4. Now you can use Synaptic to install Firefox, if you wish, and any other packages that you are in urgent need of.

5. When you are ready to exploit the potential of your actual graphics chip or card, [**[color=green]here[/color]**](http://kubuntuforums.net/forums/index.php?topic=3086232.0) is a reasonable approach if you have an Nvidia or ATI graphics system.  :)

---

### Post by nowhere@cox.net on 2007-09-22
Thanks all,

The VESA driver did the trick. I got in and used the restricted package manager to install the nvidia driver and all it good.

Should all these troubles I had with the install be reported to bugzilla or something? It was far far from a clean and simply install. I am assuming someone knows about them already...

Thanks again for the help!
Eric

---

