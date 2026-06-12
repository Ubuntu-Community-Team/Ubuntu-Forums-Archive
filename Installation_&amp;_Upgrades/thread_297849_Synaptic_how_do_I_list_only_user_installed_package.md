---
title: "Synaptic: how do I list only user installed packages?"
date: 2006-11-11
forum: Installation &amp; Upgrades
---

### Post by keltren on 2006-11-11
Is there any way in Synaptic to only list user installed packages?

Over time I try out different apps, but at some point I'd like to clean up the system and uninstall all the apps that I never really used. The problem is that it's frequently damn hard to find all of those packages, so I'm looking for a way to list only those packages that I installed myself. I've looked at the filters but haven't really been able to figure out how to do this...is it even possible?

Or is there a way to list packages by initial installation date?

---

### Post by Boelcke on 2006-11-11
Hm, interesting question.  The best thing I can come up with is that, in Synaptic, you can hit File, History.  You'll have to go through it and compile your list from what's in there, as the entire history is listed there by date.

You can see what you installed though.  All the stuff that says Update was probably done by the updates.  Look for "Installed..."

---

### Post by kerry_s on 2006-11-11
In synaptic click on status.
My bag i read it to quick, it's file> history.

---

### Post by chris_nava on 2008-07-03
The issue with using the above mentioned "installed" listing is that it shows all the dependencies as well as the item I manually selected.

IMHO: A great feature would be to denote "automatically selected" for base system packages, "manually selected" for the packages I mark in the package manager and "dependency selected" for packages the package manager helpfully marks for me.  Perhaps just with with a single letter field ("A", "M" and "D") in the above mentioned log file.  This would make cleanup MUCH easier and even provide you with a manageable list of things to reinstall when moving to a new machine.

---

