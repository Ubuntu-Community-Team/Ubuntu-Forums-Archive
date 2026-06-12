---
title: "XGL and Compiz Experts Wanted!"
date: 2006-08-09
forum: Installation &amp; Upgrades
---

### Post by TJGuitarZ on 2006-08-09
Hey everyone,

I recently partitioned my computer and loaded Ubuntu. I decided I wanted to put the XGL/compiz program. I went to this thread...

> 
[http://www.ubuntuforums.org/showthread.php?t=131267](http://www.ubuntuforums.org/showthread.php?t=131267)

After I installed it, these were the initial errors (after rebooting for the first time).

> 1. Failed to start the X server.
2. Install the X server or correct GDM configuration and restart GDM.
3. X Server disabled.

I didn't know what to do, so I kept following the directions. I typed in 'the future' and it came up with the following...

> 1. /usr/bin/thefuture: line 2: gnome-window-decorator: command not found
2. /usr/bin/thefuture: line 2: compiz: command not found

A friend told me that the identifier was wrong (I have a nVidia Quadro FX 1400, the identifier was 'Default Screen') and I shouldn't put the BusID under the 'Section "Device"' tab. I made the changes and this is where I am at now upon reboot.

> GDM: Xserver not found: /usr/bin/Xgl :0 :0 -fullscreen -as -accel glxbuffer -accel xvbo -asth /var/lib/gdm/:0.xauth -nolisten top v67

Error: Command could not be executed!

When I type in the following...

> 
sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome

... I get...

> Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package compiz

Do you guys have any idea what I am doing wrong or what I need to do to fix it? Sorry for the insanely long post, but I wanted to give you experts all the information. Any help you can give me would be GREATLY appreciated! Thanks for reading.

TJ

---

