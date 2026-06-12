---
title: "How to install Dapper desktop over server install"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by zoon_unit on 2006-06-20
I've installed the LAMP server version of Dapper, but as a Linux newbie, I could really use the desktop environment as I learn the system.

What are the steps to install the desktop on top of the server?

---

### Post by mscman on 2006-06-20
Run```
sudo apt-get install ubuntu-desktop
``` to install Gnome,
```
sudo apt-get install kubuntu-desktop
``` to install KDE, or run
```
sudo apt-get install xubuntu-desktop
``` to install XFCE.  Your best bet is probably the last one, as it will give you a very lightweight desktop, or you could go even lighter and choose to install fluxbox (tutorials for which are plentiful in the forums, just do a search for 'fluxbox')

---

### Post by taurus on 2006-06-20
Pick one...
```

sudo apt-get install ubuntu-desktop <-- for Gnome window manager
sudo apt-get install kubuntu-desktop <--for KDE window manager
sudo apt-get install xubuntu-desktop <-- for XFce4 window manager

```

---

### Post by janga on 2006-06-20
Just > sudo apt-get install ubuntu-desktop When finished installing, you have to reconfigure the xserver:
> sudo dpkg-reconfigure xserver-xorg Thats it.

EDIT:
Oops. Two people faster than me. Damn, i´m slow at typing..

---

### Post by zoon_unit on 2006-06-20
I installed the Ubuntu desktop and ran dpkg-reconfigure.  But when I type "gdm" I get the following error message (6 times)

"(process:4605): GliB-CRITICAL **: g_hash_table_lookup assertion: 'hash_table != NULL' failed"

Any ideas?

---

### Post by janga on 2006-06-21
have you tried ```
startx
```?

---

### Post by rcarring on 2006-06-21
You have to run X server first to make gdm work.

---

### Post by zoon_unit on 2006-06-21
Pardon my "newbieness" but when you say I have to run X Server first, what does that mean exactly?  What command do I type?


I've already run dpkg-reconfigure

I've tried typing startx and get a blank hatched screen with an "x" mouse pointer, but that's it.  Then went back and ran gdm and still get the GLib CRITICAL error.

---

### Post by zoon_unit on 2006-06-21
Many thanks guys!   I finally got my installation up and running.  Started over and installed the LAMP server, then installed the Ubuntu desktop, ran dpkg-reconfigure, types startx.  Voila!  success. 

Now all I have to do is figure out how to configure the Apache server so it's visible on my home network.  :-)

---

