---
title: "Login screen/GDM keeps reloading"
date: 2008-10-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Leperous on 2008-10-22
Hello everyone,

Everything seems to be working great on my desktop machine, but I have a serious problem with Interpid on my laptop.

Basically, Ubuntu is currently set to log straight in and bypass the login screen. With Intrepid, it loads the menu bars, and then a split second later removes them, and attempts to reload them. It gets stuck in this loop of trying to load the bars forever. I can CTRL+ALT+F1 out and install the latest updates and whatnot.

If I 'killall gdm' and restart it, I get to the login screen. But this keeps reloading itself: I see the 'username' box, but this vanishes almost instantly too and the thing keeps reloading.

Attached is my .xsessions-error file as well; am I right in thinking there's some sort of Cairo problem here??

It's a Sony VAIO with an nVidia GO 7400 card, I've installed the 173 drivers through envyNG and everything worked fine in 8.04. Attached is my xorg.conf; I've tried using the vesa drivers instead of nvidia as well as the 177 drivers but it doesn't seem to fix it.

I'm vaguely aware that there are some nVidia problems with Intrepid but I can't seem to find much, other than 1 other person with a similar problem who didn't get anyway. If any other info is needed, or if this is better off filed as a bug report, please let me know! Thanks.

---

### Post by Leperous on 2008-10-22
I've installed KDM: this lets me log-in okay, but then I get an empty desktop (no panels, icons, mouse moves but no right-click menu).

---

### Post by jfernyhough on 2008-10-22
Have you tried logging in with the GNOME failsafe session?

---

### Post by Leperous on 2008-10-22
I can get into the root shell prompt just fine, but I'm not sure how to get into failsafe GNOME from there: Google just throws up pages of people's problems but no practical information on *how* to do this.

Like I said the login window only appears for a split second (before reloading itself) so I'm unable to choose it from the session menu. (It usually logs me straight into Ubuntu, I only get the login prompt if I restart X.)

I can of course start an x Server fine, and try to load Nautilus, gnome-panel etc. from there, but these throw up more libcairo errors. For Nautilus, the root shell says
> 
dlopen: /usr/lib/xorg/modules/extensions//libglx.so: cannot open shared object file: No such file or directory
(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
(EE) Failed to load module "glx" (loader failed, 7)

and then the libcairo error is
> 
nautilus: symbol lookup error: /usr/lib/libgdk-x11-2.0.so.0: undefined symbol: cairo_format_stride_for_width

This in particular could be related to [https://bugs.launchpad.net/ubuntu/+bug/255660](https://bugs.launchpad.net/ubuntu/+bug/255660) which I'm looking into.

---

### Post by Leperous on 2008-10-22
Yes, the solution presented at that link seemed to fix this!

I had installed separate Cario lib files in /usr/local/lib (in particular for the VisIt plotting tool that I use for work). Removing these (libcairo* and libpango*) and rebooting the system fixed it all!

(Posted here for other people with a similar problem.)

---

### Post by jfernyhough on 2008-10-22
--edit
Not needed now. :)

---

