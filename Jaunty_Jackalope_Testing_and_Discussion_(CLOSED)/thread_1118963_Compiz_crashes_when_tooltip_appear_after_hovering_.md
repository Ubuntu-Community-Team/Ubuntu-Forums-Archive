---
title: "Compiz crashes when tooltip appear after hovering an application's icon"
date: 2009-04-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hype on 2009-04-07
Hi there,

i just call for help, as i'm stuck with a nasty bug i had since yesterday, and just managed to find the cause.

 As seen in the title, when i leave my mouse on a icon that provides a tooltip, as the tooltips displays , compiz crashes.
 
 It happens when i hover any tray-icon (xchat, pidgin), or gnome menus ("Applications, Places, System").

My problem is that the only info i get is:

Segmentation fault (core dumped)

How is it possible to have compiz be more verbose about the error?
Are there any setting that manages tooltips one the compiz side ? (via ccsm; maybe a settings problem?)

I tried to fill a bug on LP, but the servers seem loaded :]

---

### Post by hype on 2009-04-07
Ok, i'm getting closer :p

*I went back to the default settings: the crash didnt happen anymore.
*I activated plugins i usually use one by one, and tested the tooltips.

When i activated "opacity" plugin, ccsm crashed.
After reloading compiz, the "tooltip crash" came back.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/357195](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/357195)

---

