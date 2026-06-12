---
title: "Gutsy breaks kdm/gdm"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by dmonty on 2007-10-19
After Upgrading to Gutsy kdm and gdm will not allow me to log in.

When I log in the login dialog disappears and I see the blue wallpaper (kde) or brown (gnome).  After a few minutes it kicks back to the login screen.

If I shutdown the login manager and start kde manually it work fine:

xinit /usr/bin/ssh-agent /usr/bin/startkde -- :0


What is wrong with kdm/gdm to make them both lock up when trying to start the window manager?

I've tried the following:
kdm=>kde
kdm=>gnome
gmd=>kde
gdm=>gnome

I don't think it is my xorg.conf because X starts up and works file as is.  When I start kde with xinit my dual screen works fine as well as 3d acceleration works great.

I have an ATI AX550 card usging the fglrx driver.

---

### Post by tai133 on 2007-10-20
I was unable to log in  to the Gutsy gui with my ATI9600 video card. In the Gutsy Release Notes there is an entry concerning incompatibility with some ATI cards. I changed to an older NVidia card I had and everything worked fine (after configuring xorg.conf for NVidia).

---

### Post by api2001 on 2008-01-09
Hey dmonty,

I have the same problem here with a Nvidia dual screen system. What I found out is that if I disable the dual screen mode in /etc/X11/xorg.conf everything works well, but on one screen only :(

As soon as I enable dual screen mode, I have the cannot-login-in-KDE problem.

Did you find any good solution except logging in manually with xinit?

Bye APi

---

