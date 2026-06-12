---
title: "Gnome crash after update"
date: 2009-09-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Tompalaz on 2009-09-01
Today i've got a update of gnome-data.
After reboot cnome-panel crash.
The panel flashes and I have to run killall gnome-panel. When I try to start it again:
> tomas@MacintoshLinux:~$ gnome-panel

(gnome-panel:7347): libglade-WARNING **: could not find glade file '/usr/share/gnome-panel/glade/clock.glade'

** ERROR **: /usr/share/gnome-panel/glade/clock.glade not found; this installation is incorrect.
aborting...
Trace/breakpoint trap (core dumped)

---

### Post by Sub101 on 2009-09-01
OK, so we both created a thread on the same issue at the same time. I would suspect it will be fixed on another upgrade.

---

### Post by taavikko on 2009-09-01
dmesg is also showing funny flood caused by this.
It should be resolved in an hour or two.
When the transition to newer upstream version is complete and all packages are uploaded to repos.

EDIT// newer version is built and done, it's uploaded to repos and should be available in next sync.
Repos are synced once in an hour period.

---

### Post by taavikko on 2009-09-01
Fixed, by the gnome-panel* 2.27.91-0ubuntu2

---

