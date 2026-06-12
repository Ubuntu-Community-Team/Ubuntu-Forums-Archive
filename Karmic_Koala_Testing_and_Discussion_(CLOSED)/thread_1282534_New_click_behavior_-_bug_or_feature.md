---
title: "New click behavior - bug or feature?"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by froggyswamp on 2009-10-04
Folks, GTK+ widgets (i.e. the up button in Nautilus) stop responding to mouse clicks unless I move the mouse after each click.
Is it a bug or a feature?
If a feature please post a link about the reason behind it.

---

### Post by ermeyers on 2009-10-04
If you can't fix it, flaunt it -- It's a feature!

---

### Post by Jay_Bee on 2009-10-04
It's a bug and it should be reported

---

### Post by froggyswamp on 2009-10-04
> **Jay_Bee said:**
> It's a bug and it should be reported

OK, thanks, anyone willing to report it?
otoh I can't believe the Gnome devs wouldn't noticed it yet.

---

### Post by drs305 on 2009-10-04
**Edit:** 23meg found a duplicate. No need to confirm or add to this bug report.

I did not find a specific instance of this behavior reported as a Karmic bug. I've confirmed it on my Karmic Beta install and submitted a report. Feel free to add to it. Filed it via "ubuntu-bug nautilus" although as mentioned it could be part of a GTK + widgets problem.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/442444]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/442444")

---

### Post by 23meg on 2009-10-04
> **froggyswamp said:**
> OK, thanks, anyone willing to report it?


You should report it, since *you* are experiencing it. It's most likely connected to *your* input hardware or configuration, thus others may not be able to present details regarding those if asked for.

---

### Post by froggyswamp on 2009-10-04
> **drs305 said:**
> I did not find a specific instance of this behavior reported as a Karmic bug. I've confirmed it on my Karmic Beta install and submitted a report. Feel free to add to it. Filed it via "ubuntu-bug nautilus" although as mentioned it could be part of a GTK + widgets problem.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/442444]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/442444")

Yep, but it also happens in other GTK+ apps, like when clicking the "increase view size" button in an image viewing program and in other cases.

---

### Post by 23meg on 2009-10-04
> **23meg said:**
> You should report it, since *you* are experiencing it. It's most likely connected to *your* input hardware or configuration, thus others may not be able to present details regarding those if asked for.

Actually, in this case, you shouldn't file a new one, since multiple bugs are being filed on what looks like the same issue. I've marked two as duplicates of [bug #441905]("https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/441905").

---

### Post by froggyswamp on 2009-10-04
Thanks, good to know it's already reported and importance is 'high'. Though it looks like it's not yet 'confirmed'.

---

### Post by 23meg on 2009-10-04
> **froggyswamp said:**
> Thanks, good to know it's already reported and importance is 'high'. Though it looks like it's not yet 'confirmed'.

Right, I set it as "High", since if found to be a non-transient issue upon being triaged, it has severe impact on pretty much every core component (actually, even "Critical" may be justified). But bug importance should really not be interpreted independent of status. "High" importance, in combination with a status of "New" means "This bug report has just been filed, and hasn't yet been evaluated; if it turns out to be an actual bug in the code, it will be of "High" importance".

---

### Post by Ichtyandr on 2009-10-04
I noticed the same behaviour on Totem player, with play/pause button

---

### Post by chrisccoulson on 2009-10-04
Urgh, definately a bug!

---

### Post by ubername on 2009-10-05
Now fixed

---

### Post by drs305 on 2009-10-05
> **ubername said:**
> Now fixed

Just ran all the updates and rebooted. Wasn't fixed for me (64-bit). Did you happen to move the mouse a pixel or two when testing it?

---

### Post by VMC on 2009-10-05
It was **not** fixed for me either. Thanks for the bug reporting. I signed "effects me too" on it.

---

### Post by buzzmandt on 2009-10-05
It's not fixed for me either, and what's worse it's happening in kubuntu. kpatience and in wine playing diablo 2

definately a bug and not restricted to gnome.

heading to the links for launchpad to report my findings.

---

### Post by buzzmandt on 2009-10-05
the bug report link seems specifically for gtk

should i file a new bug report under kubuntu?

---

### Post by gali98 on 2009-10-05
This particular bug *is* fixed. 
If you are using a mirror other than the main server, it may take a while for packages to propigate to the mirrors. (This was my problem.)

If you are having the same problem in Kubuntu, then the bug is probably in QT, and yes definately file a bug if one is not already filed.
Kory

---

### Post by VMC on 2009-10-05
Yes, it is now fixed! But for the life of me I couldn't find the package listed on the bug report [441905]("https://bugs.launchpad.net/ubuntu/+bug/**_441905_**"),
"package gtk+2.0 - 2.18.1-1ubuntu1"

---

### Post by 23meg on 2009-10-05
> **buzzmandt said:**
> the bug report link seems specifically for gtk

should i file a new bug report under kubuntu?

If you get similar behavior under Kubuntu, that's certainly a different bug, despite having the same symptoms, so yes.

---

