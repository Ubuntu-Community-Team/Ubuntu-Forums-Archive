---
title: "Flurry screen saver disappeared from last update"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by olavjunior on 2008-10-08
Where's it gone??
Suddenly I also had xscreensaver also, but that one is removed..

---

### Post by Luffield on 2008-10-18
I just noticed this. I really miss this screensaver, it was beautiful.

---

### Post by PinkFloyd102489 on 2008-10-19
Just noticed it also, I want it back.

---

### Post by autocrosser on 2008-10-20
I had that too--Look to see which file is missing:

flurry--/usr/lib/xscreensaver
flurry.desktop--/usr/share/applications/screensavers
flurry.xml--/usr/share/xscreensaver/config

I have a older, un-updated version of Intrepid as a backup, before Flurry went missing & I just compared/reinstalled it--I don't remember which file was not there--if anyone wants the missing file---just tell me which one is needed & I'll post it.

---

### Post by olavjunior on 2008-10-21
the first and the last! Would be nice if you posted them!

---

### Post by aethralis on 2008-10-21
Hmm.. it was my screensaver too...

---

### Post by kahlil88 on 2008-10-21
I don't really believe in screensavers, but the Flurry is probably my favorite. How sad!

---

### Post by autocrosser on 2008-10-21
OK--I made .tars of both--just put them in where they belong & then either logout/in or reboot to check--
please report if they work for you--you might need to chmod 777 them for your system.....

> **olavjunior said:**
> the first and the last! Would be nice if you posted them!

---

### Post by autocrosser on 2008-10-21
If that works for you---We might think of a bug report. I would like the reason that Flurry was dropped--oversight or ?

---

### Post by Avoozl on 2008-10-22
Mine had disappeared as well (first and last file) so I copied the two you uploaded and it's back!  No log out or reboot necessary.  Thanks!

---

### Post by autocrosser on 2008-10-22
No problem--I have used Flurry for years & HATED to not have it--so I was motivated to get it fixed. Glad I could help.....

---

### Post by Limulus on 2008-10-24
> **olavjunior said:**
> Where's it gone??
Suddenly I also had xscreensaver also, but that one is removed..

I am not exactly sure why, but I suspect it has to do with a bug ([https://bugs.launchpad.net/ubuntu/+source/xscreensaver/+bug/224065](https://bugs.launchpad.net/ubuntu/+source/xscreensaver/+bug/224065)) involving Flurry completely locking up Intel graphics-based computers.

Hopefully they'll get it sorted out soon; I miss it too :(

---

