---
title: "xserver want to remove nvidia-glx-190"
date: 2009-12-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dino99 on 2009-12-07
lot of changes with xserver: have to wait before installing that dependencies were resolved.

---

### Post by jppr on 2009-12-07
there is all new X ;) nvidia-glx-185 works fine

---

### Post by SevenMachines on 2009-12-08
seems like glx-185 wants to uninstall the new xorg for some reason, but if you rebuild the package it all install fine

---

### Post by afv on 2009-12-08
> **SevenMachines said:**
> seems like glx-185 wants to uninstall the new xorg for some reason, but if you rebuild the package it all install fine

I managed to install it using the 195 version from your [_Nvidia PPA_](https://launchpad.net/~sevenmachines/+archive/nvidia?field.series_filter=lucid). Thanks. ;)

---

### Post by SevenMachines on 2009-12-08
> **afv said:**
> I managed to install it using the 195 version from your [_Nvidia PPA_]("https://launchpad.net/%7Esevenmachines/+archive/nvidia?field.series_filter=lucid"). Thanks. ;)
Seems a good time to add my usual warnings about lack of knowledge and quality control in any of my ppa's :) and to remind people about nvidia maintainer [Mario Limonciello's ppa]("https://edge.launchpad.net/%7Esuperm1/+archive/ppa"). Who's packaging I shamelessly hack when I need to play around with newer nvidia beta versions

---

### Post by dino99 on 2009-12-09
> **afv said:**
> I managed to install it using the 195 version from your [_Nvidia PPA_](https://launchpad.net/~sevenmachines/+archive/nvidia?field.series_filter=lucid). Thanks. ;)

If nvidia-vdpau repo was used previously, you have to deactivate it to avoid conflict when installing nvidia-glx-195

( due to overwriting warning in /usr/lib/...)

Good work from "sevenmachines"

---

### Post by philinux on 2009-12-09
I was using 185 so I deactivated it to let the xserver upgrade go ahead.

Guess I'll have to wait now for things to catch up.

---

### Post by LKjell on 2009-12-09
Anyone having problem with the 195 driver and the new xorg? I have to boot in recovery mode and startx twice to boot. If I do a normal boot the whole machine looks like to go in a loop.

---

### Post by autocrosser on 2009-12-09
All "seems" to be good here---no problems with the 195 driver, Xorg & restarting....SevenMachines PPA saves the day!!!!!!

---

### Post by LKjell on 2009-12-10
The problem was 3D acceleration was disabled some how. Needed to add video group to the user.

---

### Post by ubername on 2009-12-10
Not sure if this is the same problem, but I can't boot into a GUI at all now. I was using 195.22, (having some problems on wake from suspend but otherwise fine). Recent updates now mean I boot into tty1 (I think) and 'sudo startx' gives something like 

error 3 can't find usr/bin/X

gdm gives the messages like
server only lasted.098 seconds 
a number of times.

any clues on how to fix (from the command line - I don't know how to add repos etc with out synaptic, I'm ashamed to say!)

---

### Post by SevenMachines on 2009-12-10
looks like xorg was uninstalled, try,
$sudo apt-get install xorg

---

### Post by ubername on 2009-12-10
> **SevenMachines said:**
> looks like xorg was uninstalled, try,
$sudo apt-get install xorg

Sorted, thanks!

---

### Post by SevenMachines on 2009-12-11
is there a bug opened on the 185 driver? it only needs a rebuild, seems to be causing a lot of people problems

---

### Post by philinux on 2009-12-11
> **SevenMachines said:**
> is there a bug opened on the 185 driver? it only needs a rebuild, seems to be causing a lot of people problems

Yep, just found it.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/494166](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/494166)

---

