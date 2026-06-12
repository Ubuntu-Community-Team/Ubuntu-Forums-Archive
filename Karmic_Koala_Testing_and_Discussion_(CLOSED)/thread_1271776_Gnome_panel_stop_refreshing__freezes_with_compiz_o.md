---
title: "Gnome panel stop refreshing / freezes with compiz on ubuntu karmic"
date: 2009-09-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nIRV on 2009-09-21
On ubuntu karmic, my gnome panel freezes after a while (i.e. applets on panel not redrawn, hover effect on clock applet not drawn, etc. etc.). This happens usually 5 minutes into a seesion.

This is a problem that has been visible to me since as long as I can remember.

Anybody else having same issue?

---

### Post by Sand &amp; Mercury on 2009-09-21
It's strange that it's doing that so often. Whenever it's happened to me, I've just run killall gnome-panel and it comes good again. Running Jaunty, it's only ever frozen up when changing themes for me. So maybe the problem lies somewhere in either the panel itself or the gnome settings daemon.

---

### Post by alexmurray on 2009-09-21
For me it happens when I kill and restart gnome-do - weird I know, but I can pretty much reproduce it by doing a killall gnome-do && gnome-do - then my top gnome panel stops updating - NOTE: my top panel is not expanded... perhaps this has something to do with it?

---

### Post by nIRV on 2009-09-26
Have you guys found a bug number for this issue?

---

### Post by Amaranth on 2009-09-26
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/342980](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/342980)

Without steps I can reproduce there is basically no chance of this bug getting fixed except by accident though.

---

