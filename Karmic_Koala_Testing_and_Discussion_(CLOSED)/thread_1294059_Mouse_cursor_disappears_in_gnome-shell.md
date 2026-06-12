---
title: "Mouse cursor disappears in gnome-shell"
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by samjh on 2009-10-17
Just after the latest bunch of upgrades, my mouse cursor disappears whenever it moves over the activities bar (the black bar at the top of the screen) and the side menu.

Is anyone else suffering from this problem?

---

### Post by Merk42 on 2009-10-17
How are you building gnome-shell? I always do it from source, but I heard there was some Karmic packages?
Does it disappear when not using gnome-shell, if so wouldn't this be a gnome-shell bug an not an Ubuntu/Karmic one?

---

### Post by samjh on 2009-10-18
There is a package called gnome-shell in Karmic, so you don't need to build it yourself (unless if you want the latest git release).

The cursor only disappears when gnome-shell is running.  I'm curious to see if this is a problem only for me, or if it is actually a bug in gnome-shell.  If others are suffering the same problem, then I'll lodge a bug report with the gnome devs, but otherwise there is no point.

---

### Post by deepeis on 2009-10-19
> **samjh said:**
> There is a package called gnome-shell in Karmic, so you don't need to build it yourself (unless if you want the latest git release).

The cursor only disappears when gnome-shell is running.  I'm curious to see if this is a problem only for me, or if it is actually a bug in gnome-shell.  If others are suffering the same problem, then I'll lodge a bug report with the gnome devs, but otherwise there is no point.

I have the same problem. I am using Karmic and the self built Gnome-Shell.

Best wishes

Deepeis

---

### Post by aethralis on 2009-10-19
I'm using gnome-shell from the repo and having no problems with the mouse cursor.

---

### Post by ago on 2009-10-20
Same here, it depends how you start it.

With 'gnome-shell --replace' the mouse pointer works well

If I set gnome-shell as default desktop manager in gconf then gnome-shell elements hide the pointer as if the pointer was in a lower layer.

---

### Post by manoriax on 2009-10-21
> **ago said:**
> Same here, it depends how you start it.

With 'gnome-shell --replace' the mouse pointer works well

If I set gnome-shell as default desktop manager in gconf then gnome-shell elements hide the pointer as if the pointer was in a lower layer.

Same problem here.

---

### Post by ago on 2009-10-21
[https://bugs.edge.launchpad.net/gnome-session/+bug/457046](https://bugs.edge.launchpad.net/gnome-session/+bug/457046)

I filed against gnome-session since there is no gnome-shell project at the moment (unless I missed it).

---

### Post by simius on 2009-10-21
As a workaround, try: alt-f2, 'restart', enter.

---

### Post by manoriax on 2009-10-21
Thank you.

---

### Post by manoriax on 2009-10-24
Well, urm, seems to be working since I've applied all the recent updates.

---

### Post by shafin on 2009-10-24
> **ago said:**
> Same here, it depends how you start it.

With 'gnome-shell --replace' the mouse pointer works well

If I set gnome-shell as default desktop manager in gconf then gnome-shell elements hide the pointer as if the pointer was in a lower layer.
Same here.

---

