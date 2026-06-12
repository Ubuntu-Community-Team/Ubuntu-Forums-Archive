---
title: "How do I remove the desktop"
date: 2016-05-21
forum: Installation &amp; Upgrades
---

### Post by tomdean@speakeasy.org on 2016-05-21
I prefer to operate using X and twm.

I have 16.04 on sda and 14.04 on sdb.  I normally use 14.04 and installed 16.04 to try the desktop and look to upgrading.

I want to remove lightdm and the desktop from 16.04.  How do I do this?  How much should I remove?

```
sudo apt-get purge alacarte gir1.2-gconf-2.0 gir1.2-panelapplet-4.0 \
  gnome-applets gnome-applets-data gnome-control-center \
  gnome-control-center-data gnome-media gnome-panel gnome-panel-data \
  gnome-session gnome-session-flashback gnome-settings-daemon \
  gstreamer0.10-gconf indicator-applet-complete \
  libgnome-media-profiles-3.0-0 libgoa-backend-1.0-1 \
  libpanel-applet-4-0 metacity notification-daemon -s

```

On my 14.04 system, the start sequence is:

```
init --> login
   login --> startx
     startx --> xinit
       xinit --> X
       xinit --> xterm (console)
         xterm(console) --> twm
         xterm(console) --> xterm and etc.

```
How do I get a similar result in 16.04?

---

### Post by grahammechanical on 2016-05-21
You might be better off using the mini ISO image for installations. That will install Linux and nothing more unless we specify exactly want we want installed either at the time of the installation or after installation.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Better not to install a certain desktop environment in the first place than try to remove it afterwards.

Regards

---

