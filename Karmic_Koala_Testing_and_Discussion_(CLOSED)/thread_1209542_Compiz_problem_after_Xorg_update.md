---
title: "Compiz problem after Xorg update"
date: 2009-07-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by wayne_cat on 2009-07-10
I don't have errors in Xorg.0.log and DRI seems to work:

```
root@macbook:/var/log# glxinfo |grep rendering
direct rendering: Yes
root@macbook:/var/log# 

```but the system is slow like hell and Xorg is running with 15 to 20% CPU usage.

edit: forgot so say : ATI Technologies Inc M56P [Radeon Mobility X1600]

---

### Post by BwackNinja on 2009-07-10
Remember, swrast is direct rendering too, so you can't go by that alone. Check the Opengl renderer string

"glxinfo | grep renderer"

---

### Post by wayne_cat on 2009-07-10
not a Compiz problem ... Avant Window Navigator is sick at the moment . Gazillions of error messages in .xsession-errors

```
(awn:14935): Gdk-CRITICAL **: gdk_region_destroy: assertion `region != NULL' failed
```

---

### Post by Vanishing on 2009-07-10
> **wayne_cat said:**
> not a Compiz problem ... Avant Window Navigator is sick at the moment . Gazillions of error messages in .xsession-errors

```
(awn:14935): Gdk-CRITICAL **: gdk_region_destroy: assertion `region != NULL' failed
```

+1 confirm...
anyway arround that?

---

### Post by budluva04 on 2009-07-10
<ubottu>	Launchpad bug 398008 in avant-window-navigator "awn uses 100% cpu" [Undecided,New] [https://launchpad.net/bugs/398008](https://launchpad.net/bugs/398008)

ya this is known guys...also, have you guys tried out Gnome-Do's Docky skin? much better dock than awn, give it a go, beats awn and other docks hands down

---

### Post by Vanishing on 2009-07-10
> **budluva04 said:**
> <ubottu>	Launchpad bug 398008 in avant-window-navigator "awn uses 100% cpu" [Undecided,New] [https://launchpad.net/bugs/398008](https://launchpad.net/bugs/398008)

ya this is known guys...also, have you guys tried out Gnome-Do's Docky skin? much better dock than awn, give it a go, beats awn and other docks hands down

well...that bug is still new and undecided..

yesh, i use gnome-do, but i still like to use avant:lolflag:

---

### Post by wayne_cat on 2009-07-10
> **budluva04 said:**
> <ubottu>    Launchpad bug 398008 in avant-window-navigator "awn uses 100% cpu" [Undecided,New] [https://launchpad.net/bugs/398008](https://launchpad.net/bugs/398008)

ya this is known guys...also, have you guys tried out Gnome-Do's Docky skin? much better dock than awn, give it a go, beats awn and other docks hands down

thank you for the link to the launchpad bug report.

I have tried different docks ... still prefer awn.

---

### Post by wayne_cat on 2009-08-08
*bump*

there is a fixes AWN version. You can get it here:

[https://launchpad.net/~gilir/+archive/updates]("https://launchpad.net/%7Egilir/+archive/updates")

Works great ... please test it and report bugs and problems in the bug report:

[https://bugs.launchpad.net/ubuntu/+source/avant-window-navigator/+bug/398008](https://bugs.launchpad.net/ubuntu/+source/avant-window-navigator/+bug/398008)

---

