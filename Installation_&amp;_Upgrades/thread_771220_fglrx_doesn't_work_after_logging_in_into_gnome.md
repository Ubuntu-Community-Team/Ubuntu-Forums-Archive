---
title: "fglrx doesn't work after logging in into gnome"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by ayampanggang on 2008-04-27
Hello all,

I've just done the upgrade to hardy, and i faced a few problems which may be related:

1. gdm login problem: After booting the system and just before gdm starts, the message *The greeter application seems to be crashing. Attempting to use a different one* will always appear and i was forced to do CTRL+ALT+BACKSPACE to restart X. gdm will be started successfuly after this restart process.

According to most solutions, this is caused by the accessible login feature found in gdm, and they suggest to disable it-which i did, yet it still crashes. I am also sure that i have more than adequate space on /boot and root FS, and this mustn't be the source of problem. (i have 71MB / 100MB free on /boot, and 90GB on root FS)

2. fglrx problem: fglrx only works when i log into **failsafe gnome mode**. When i log into **normal gnome session**, it automatically switches to mesa driver.

For the second problem, this is the detailed events that happens after i tried to log into **normal gnome sessions**:
1. X will always crashes and restarted automatically. Then it prompts me with the login screen again.
2. After i log into the **normal gnome session**, the driver used is mesa instead of fglrx. If i had tried to log into the **failsafe gnome** instead, it correctly uses fglrx instead of mesa.

My guess for the **fglrx problem** is as follows: When i attempted to login using **normal gnome session** for the first time, X somehow crashes, and X automatically switches to mesa. Then the second time i log in, it uses mesa instead of fglrx. 

My question is, why did logging in with **normal gnome session** crashes, while the **failsafe** one works with fglrx??

I have searched for possible solution and found one close to my problem:
[http://ubuntuforums.org/showthread.php?t=671091&highlight=glxinfo](http://ubuntuforums.org/showthread.php?t=671091&highlight=glxinfo)
that thread is about nvidia card. basically it suggest that there's something wrong with the symlink after xorg upgrade: The /usr/lib/xorg/modules/extensions/libglx.so is not an actual libfile, but instead a symlink that should point to another lib file (e.g. libglx.so.100.14.11) in the same dir.

In my case, i have an ATI driver, and i don't see such file to exist within that directory. I tried to link it to **/usr/lib/fglrx/libGL.so.1.2.xlibmesa** but fglrxinfo yields
```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

Segmentation fault

```
which is of course no good. lol

And for additional information, my system is latest hardy heron, ATI Mobility X600 with manually installed fglrx (version 8.476)

I hope anyone have a clue about whats happening. This is the third day i'm fighting with this and so far have not found any feasible solution...

thank you in advance.

---

### Post by ayampanggang on 2008-04-27
&%^%%## fixed the second problem by simply removing my old, dangling XGL. This IS the cause of my second problem! I can't believe it since i removed the script for autostarting XGL at startup. ubuntu must have cached it somewhere. I felt happy and stupid at the same time.

Now first problem is the only remaining. Anyone knows what causes this aside from accessible login feature and full hard disk?

Thank you

---

### Post by gerben1 on 2008-04-27
wow this maybe the reason for my problem too, whatever I tried tutorials, envyNG I always end up with:

gerben@CC1184274-A:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

Can you explain how you got rid of XGL?

---

### Post by ayampanggang on 2008-04-27
well just do sudo aptitude remove xserver-xgl

hope that helps you

---

### Post by fishtoprecords on 2008-04-28
you can also try booting in recovery mode, and running
xfix

which did wonders for my system, which is a Lenovo T60p with a separate ATI card. The standard install worked only in VGA mode.

---

