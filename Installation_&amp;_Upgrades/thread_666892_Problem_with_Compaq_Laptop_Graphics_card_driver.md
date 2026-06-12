---
title: "Problem with Compaq Laptop Graphics card driver"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by avilanchee on 2008-01-13
Guys ,

Laptop Model : Comapq Presario V3604TU, Integrated intel GMA X3100 graphics card on intel 965 chipset family. Gusty identifies and loads a Intel experimental driver. I couldnt activate the 3D acceleration and effects. Please help me installing the appropriate divers.

Aslo wud be hepful if someone help me in configuring WLAN (broadcom )

thanks in advance 
Avinash

---

### Post by agim on 2008-01-13
hi avilanchee. I have a similar computer and I just started using ubuntu as well. As far as the 3d graphics go, our graphics card, the intel 965, has been blacklisted for use with compiz.
You can work around it, but it doesn't do all of the nice effects. On my computer I can get the desktop cube to work and a few other things, but the rain affect and some others just don't work, and sometimes screw things up to the point that I have to logout and log back in to turn it off.

Here are the steps I took.

First go to the Synaptic Package Manager, search compiz

click to install the package 'compiz' and the package 'compiz-gnome'.

Click apply

then open a terminal and type this

sudo gedit ~/.config/compiz/compizconfig/config

Enter your password if it asks you to.

At the begining of the file type

SKIP_CHECKS=yes

go to file -> save
then exit.

After that, go to System -> Preferences -> GL Desktop (I assume here that you are using ubuntu, and not xubuntu or kubuntu)

When the window opens, click on the box that says 'enable GL Desktop'

and that should fix that problem.

As far as your broadcom card goes...

open a Terminal and type

lspci | grep Broadcom

to find out which Broadcom card you use. And we could go from there.

If you want to look up the rest yourself you will need to look up a program called ndiswrapper either here on the forums or with google. But you can feel free to ask again here.

Good luck.

---

