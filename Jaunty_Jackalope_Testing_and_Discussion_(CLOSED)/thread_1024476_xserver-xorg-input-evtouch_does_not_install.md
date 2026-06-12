---
title: "xserver-xorg-input-evtouch does not install"
date: 2008-12-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by vishalrao on 2008-12-29
Just got kernel .28-4.5 and running nvidia 180.18 beta with IgnoreABI with xorg 1.5.99xxx - at least the desktop is stable.

I wanted to try touchscreen on my tablet but the xserver-xorg-input-evtouch synaptic package installation wants to uninstall a bunch of other packages, and it shows "c" (conflict?) in aptitude console listing.

I noticed in the jaunty-changes mailing list archive the source package xf86-input-evtouch was updated on Dec 15th for the new xorg server version.

I'm using the Japanese RIKEN archive mirror which I believe should only be a few hours behind.

My question is should I just wait for the package to become available or is it appropriate/polite to email ubuntu-devel-discuss (or where? or file a bug?) and ask for that package to be updated ASAP so I can test?

edit: doh, RIKEN mirror is now showing 1 week behind :(

---

### Post by tepsipakki on 2008-12-29
evtouch doesn't build against the new xserver, but the evdev driver has touchscreen support now, so you should try it instead (it should be used by default anyway).

---

### Post by vishalrao on 2008-12-29
input-evdev appears to be installed but i dont know what to do to set it up. in intrepid when i installed the evtouch package, i got a "calibrate touchscreen" applet in my system->prefereces menu.

is there some other package i can install for touchscreen config/setup or documentation i can look at? /usr/share/doc/xserver-xorg-input-evdev just has a copyright file.

(i have an hp pavilion tx1302au tablet)

---

### Post by vishalrao on 2008-12-29
Oh looks like an "FTBFS" ? [https://launchpad.net/ubuntu/+source/xf86-input-evtouch/0.8.7-4build2/+build/813522](https://launchpad.net/ubuntu/+source/xf86-input-evtouch/0.8.7-4build2/+build/813522)

So should I wait or notify someone?

edit:

Reported [lpbug]312098[/lpbug] at [https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/312098](https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/312098)

Just re-read tepsi's post above, lol, looks like devs are already aware of it :)

---

### Post by ShirishAg75 on 2008-12-29
vishal, 
    "FTBFS" is slang/leetspeak/netspeak for '**F**ailed **T**o **B**uild **F**rom **S**ource'

---

