---
title: "Quick question regarding X startup!"
date: 2005-08-21
forum: Installation &amp; Upgrades
---

### Post by blastus on 2005-08-21
In setting up the drivers for my nVidia card I used the instructions posted at [http://ubuntuguide.org/](http://ubuntuguide.org/) and they worked fine. However, everytime I boot up I need to open the NVIDIA Settings program or enter in "nvidia-settings --load-config-only" to get the settings to load.

My question is how do I get the "nvidia-settings --load-config-only" command to run everytime I boot up? How do I get something like this to run everytime I boot up with X.Org in Ubuntu or with XFree86 in Mepis??? What file do I edit?

---

### Post by nad on 2005-08-21
/etc/X11/Xsession for global configuration or ~/.bash_profile for yourself.

/usr/share/doc/NVIDIA_GLX-1.0/nvidia-settings-user-guide.txt for details.

---

### Post by blastus on 2005-08-21
I tried editing the /etc/X11/Xsession before...nothing happens. I tried editing the /etc/X11/xinit/xinitrc file...nothing happens. I tried creating a ~/.xinitrc file...nothing happens. I've tried rebooting several times...nothing happens. There doesn't seem to be a way to load any X applications on startup!

And isn't the Bash profile just used for shell access? Doesn't Bash get loaded before X? So if I put something inside my Bash profile doesn't it have to be a shell program? I need to be able to run an X application on startup. I don't know maybe I'm confusing something but I don't think you can load X applications from a Bash profile when X starts.

What if I wanted gedit to load on startup? This is my /etc/X11/xinit/xinitrc file...

```

#!/bin/sh
# $Xorg: xinitrc.cpp,v 1.3 2000/08/17 19:54:30 cpqbld Exp $

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
. /etc/X11/Xsession

```

How or what do I put where to get gedit to load? i've tried... 

```

. /etc/X11/Xsession
gedit &

```

...and 

```

gedit &
. /etc/X11/Xsession

```

...nothing happens. I've even tried joining the commands ". /etc/X11Xsession && gedit &"...nothing happens. I also tried taking out the "&" so that gedit is not a background task...nothing happens. And I've rebooted several times...nothing happens. 

As far as /etc/X11/Xsession is concerned I've tried putting in a "gedit" command in many places in the file even before the exit 0 command...NOTHING HAPPENS. I don't know why this has to be so complicated. How I would I run an application like "gedit" on startup on Hoary? I'm just trying to get gedit to load on startup first because it is easier to test than the nvidia settings loading. I've looked all over the web for info on this and can't figure it out. Does ANYONE know how to do this?  ](*,)

---

### Post by nad on 2005-08-21
I am not at a hoary computer at the moment, so, you may wish to look at /etc/gdm/gdm.conf .

---

