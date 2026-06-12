---
title: "Installing X-Server on Ubuntu Server Edition"
date: 2007-07-03
forum: Installation &amp; Upgrades
---

### Post by thepurpleblob on 2007-07-03
I have installed Ubuntu Server Edition (Feisty) and it all works fine.

I want to install XServer, mostly so that I can run X11 applications to view remotely.

Anyway, I searched for documentation and it all seems very conflicting, but in the end I ran

sudo apt-get install ubuntu-desktop

This downloaded a lot of stuff, but I don't know what to do next. I want the server to start at boot like a desktop system and I want any user to be able to do...

ssh -X my.machine.com

but I can't find any likely looking start script in /etc/init.d/ I did try running 'sudo startx', but that just gives lots of errors. 

Any help or pointers to documentation appreciated. Google searches seem to mostly return people having problems!

---

### Post by moore.bryan on 2007-07-03
*if you wanted a bare-bones box, the ubuntu-desktop probably wasn't the way to go.  have you installed x-window-system-core, xserver-xorg, and xbase-clients?*

---

### Post by louieb on 2007-07-03
This is how I added  x to  my server [HOWTO: Leightweight Gnome - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=298818&highlight=xorg+gdm+gnome-core")

---

