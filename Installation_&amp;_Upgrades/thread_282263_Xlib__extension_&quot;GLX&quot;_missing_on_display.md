---
title: "Xlib:  extension &quot;GLX&quot; missing on display &quot;:0.0&quot;."
date: 2006-10-22
forum: Installation &amp; Upgrades
---

### Post by Robbi_az on 2006-10-22
Hello, 

Very new to Ubuntu... currently running KDE !
Trying to set up Video card so i can install XGL+Beryl...

If i run the dpkg-reconfigure xserver-xorg and select "nv" driver... i can get the machine to boot ok and work...

However with this set up, and also whenever i try to..

[PHP]
sudo apt-get install nvidia-kernel-source
sudo apt-get nvidia-glx
sudo nvidia-glx-config enable
sudo nvidia-xconfig
[/PHP]

i still get the same message when i.. glxinfo...

[PHP]
robbi@robbi:/$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
robbi@robbi:/$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual[/PHP]

I've found literally hundreds of threads with similar issues, most of which are resolved by going in to the /etc/X11/xorg.conf and either adding Extension sections, commenting out "dri" and "GLcore", making sure "glx" is there, making sure driver read is "nvidia" not "nv" as "nv" doesn't support 3D. But still after all of this... i cannot find a solution... can anyone help me !?

I have a Geforce FX 5500 by thwe way....

---

### Post by Robbi_az on 2006-10-22
I just realised that i have a first version linux-restricted-modules for my 2.6.15-27-386

So, am downloading the most recent for my kernel. After that is installed i will purge nvidia.. and reinstall, then try to configure.. and post results.

---

### Post by taurus on 2006-10-22
Make sure you use "nvidia" driver in /etc/X11/xorg.conf.  May have to log out, restart X, and log back in again...

---

