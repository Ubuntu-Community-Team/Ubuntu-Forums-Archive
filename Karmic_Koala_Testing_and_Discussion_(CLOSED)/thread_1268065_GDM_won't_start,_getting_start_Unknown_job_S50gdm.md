---
title: "GDM won't start, getting start: Unknown job: S50gdm"
date: 2009-09-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sylwester on 2009-09-16
After the very interesting last day I managed to do an update later today and I'm up 2 date. I alsop had a look at System > Administation > Services and checked cron and some other stuff,, After reboot I get

Bla bla about converting init sctript to a upstart jobm then
start: Unknown job: S50gdm

However by starting dbus, hal and network-manager and gdm by hand I get a working system.  How does this work now. Does UBuntu use the init-script with the warning messages or is this because I was messing around with Services and there some kind of old-school stuff that broke upstart..

How does upstart work and where do I see what it should start?

---

