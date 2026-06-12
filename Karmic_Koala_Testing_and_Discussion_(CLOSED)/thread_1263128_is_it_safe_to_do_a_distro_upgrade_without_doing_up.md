---
title: "is it safe to do a distro upgrade without doing updates"
date: 2009-09-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by joshuapbell on 2009-09-10
like say going from 9.04 (fresh install) to 9.10, also can i do this via a live cd or does it have to be done through the upgrade manager?

---

### Post by fela on 2009-09-10
You can either do a fresh install via the livecd or you can run it via the update manager. A fresh install generally works better though.

---

### Post by joshuapbell on 2009-09-10
> **fela said:**
> You can either do a fresh install via the livecd or you can run it via the update manager. A fresh install generally works better though.

I can't seem to get the live disc to boot... which is why the question...


grrr it is driving me bonkers....

---

### Post by Reiger on 2009-09-10
A dist-upgrade will/should pull in the updates automatically. I've dist-upgraded from Hardy to here.

---

### Post by knarf on 2009-09-10
I have not done a fresh install on any of my machines since the dinosaurs roamed the planet, more or less. Just don't force anything, make sure the package management system is in a consistent state, purge configuration files for unwanted packages and it should work fine using dist-upgrade. Make a backup of any directories you want keep if you're afraid of what the upgrade will do to them.

This (continuous upgrade without re-install) has worked both with Redhat-based distributions as well as Debian-based ones, the latter usually more trouble-free than the former.

---

### Post by infamousrev on 2009-09-10
If its a test box, then doing just updates might do the trick.

But if your a bleeding edge addict like me using alpha as production machine you often notice that fresh installs deviate from updated versions of ubuntu on your machine.

This is most likely caused by manual workarounds from times that things brake, or other manual adjustments.

Thats why I recommend doing fresh installs. 
Moving your home folder to the new install will save most of the settings.

---

