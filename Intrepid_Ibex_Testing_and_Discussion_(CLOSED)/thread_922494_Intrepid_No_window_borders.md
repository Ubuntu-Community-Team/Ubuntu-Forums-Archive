---
title: "Intrepid: No window borders"
date: 2008-09-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Decline- on 2008-09-17
I recently upgraded from Hardy Heron to Intrepid Ibex. I first had some trouble getting hardware support, but I solved it and am now using the Nvidia 177 driver. No trouble there. The trouble is, when I enable Compiz, GTK/Window borders disappear... I do have fusion-icon, but changing between GTK and Emerald makes no difference. My only options are Compiz without borders or Metacity without Compiz... 

Any suggestions? Running "compiz --replace" in terminal gives no output...

Installed versions are:
> 
$ dpkg --list | egrep 'compiz|metacity'
ii  compiz                                     1:0.7.7+git20080807-0ubuntu9          OpenGL window and compositing manager
ii  compiz-core                                1:0.7.7+git20080807-0ubuntu9          OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.7.7+git20080807-0ubuntu1            Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.7.7+git20080807-0ubuntu1            Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.7.7+git20080807-0ubuntu9          OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.7.7+git20080807-0ubuntu9          OpenGL window and compositing manager - plug
ii  compiz-wrapper                             1:0.7.7+git20080807-0ubuntu9          OpenGL window and compositing manager, wrapp
ii  compizconfig-backend-gconf                 0.7.7+git20080618-0ubuntu1            Settings library for plugins - OpenCompositi
rc  compizconfig-settings-manager              0.7.7+git20080630-0ubuntu1            Compiz configuration settings manager
ii  emerald                                    0.7.2-0ubuntu2                        Decorator for compiz-fusion
ii  libcompizconfig0                           0.7.7+git20080807-0ubuntu1            Settings library for plugins - OpenCompositi
ii  libemeraldengine0                          0.7.2-0ubuntu2                        Decoration engines for compiz-fusion
ii  libmetacity-dev                            1:2.23.610-0ubuntu1                   Development files of lightweight GTK2 based 
ii  libmetacity0                               1:2.23.610-0ubuntu1                   library of lightweight GTK2 based Window Man
ii  metacity                                   1:2.23.610-0ubuntu1                   A lightweight GTK2 based Window Manager
ii  metacity-common                            1:2.23.610-0ubuntu1                   Shared files of lightweight GTK2 based Windo
ii  python-compizconfig                        0.7.7+git20080618-0ubuntu1            Compiz configuration system bindings


Normally I would start with xorg.conf, but in Intrepid, if I understood correctly, there would be no use for xorg.conf for these matters? Anyways here's my xorg.conf as for now:

> Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	BusID		"PCI:1:0:0"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

---

### Post by Decline- on 2008-09-17
Some new packages arrived:
compiz compiz-core compiz-gnome compiz-plugins compiz-wrapper gedit
  gedit-common landscape-client libdecoration0 libmetacity-dev libmetacity0
  metacity metacity-common update-motd xkb-data

However, they didn't fix my issue... Don't really know what to do now, running Metacity atm... :/

---

### Post by shafin on 2008-09-17
I see you have fusion-icon installed. After you enable compiz and get the borderless windows,try reloading the window manager by right clicking on the fusion-icon. Reloading solves the problem for me.

---

### Post by Decline- on 2008-09-17
Sorry, already tried that. Makes no difference...

---

### Post by Decline- on 2008-09-18
Oh solved it... window decorations were suddenly off in ccsm :P Just turned it on again...

However I have a problem with the gtk-window-decorator. That is, I'm missing the min/max/close buttons! They're just gone... no matter what theme I'm using!

---

### Post by Decline- on 2008-09-18
Omg... new problem. Just tried enabling indirect binding in fusion-icon then disabling it, testing performance... this screwed up compiz, now all I get is a box in the upper left corner, while the rest of the screen is black. + rotating cube looks awful... :popcorn:

What the hell?

[ATTACH]85667[/ATTACH]

---

