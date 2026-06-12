---
title: "Update Manager wants to reinstall everything I removed!"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by Flywaver on 2009-11-29
For some reason, since 2 days ago, the Update manager wants to run a partial upgrade in which it wants to basically install all th unneccessary apps I removed about a month ago! It basically thinks that I am running all these apps and they are outdated! 

How can I stop/prevent this bug?
I am running 9.10 with the latest updates, daily builds...everything was fine until 2 dans ago when Update Manager decided that my system was running old apps lol

---

### Post by wilee-nilee on 2009-11-29
What did you remove and what is update manager showing to reinstall

---

### Post by Flywaver on 2009-11-29
I removed all unwanted packages! 
Xsane, brasero, cups, evolution, gnome-games, samba, printer...

this should not happen. these apps were removed a month ago and I had no problem whatsoever until an update 2-3 days ago!

---

### Post by Soul-Sing on 2009-11-29
> **Flywaver said:**
> I removed all unwanted packages! 
Xsane, brasero, cups, evolution, gnome-games, samba, printer...

this should not happen. these apps were removed a month ago and I had no problem whatsoever until an update 2-3 days ago!

when you remove for instance evolution completely you remove (partly) the ubuntu-desktop. and your left with a broken system.
you could remove evolution but always let evolution-data-server(-common) untouched.

---

### Post by wilee-nilee on 2009-11-29
> **leoquant said:**
> when you remove for instance evolution completely you remove (partly) the ubuntu-desktop. and your left with a broken system.
you could remove evolution but always let evolution-data-server(-common) untouched.

+1 any time you remove anything always look at the dependencies.
Evolution can be broken from the meta desktop but I just take it off the menu.

---

### Post by Flywaver on 2009-11-29
Guys, evolution-data-server and evolution-data-server-comon were NOT removed! I did this for all packages I removed I made sure the dependencies would not affect the system!

What does gnome-games has to do with anything? I removed it on all ubuntu distros just fine lol! Same for xsane and many other apps.

This just doesn't makes any sense at all!

---

### Post by wilee-nilee on 2009-11-29
> **Flywaver said:**
> Guys, evolution-data-server and evolution-data-server-comon were NOT removed! I did this for all packages I removed I made sure the dependencies would not affect the system!

What does gnome-games has to do with anything? I removed it on all ubuntu distros just fine lol! Same for xsane and many other apps.

This just doesn't makes any sense at all!

Sorry we are not Karnac, we can't read your mind; you give vague information, and when asked for confirmation you don't give the full information then you post this last answer which is just plain garbage good bye and good luck getting any help.

---

