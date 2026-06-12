---
title: "Intrepid upgrade breaks Fluxbuntu gksu"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by snowpine on 2008-10-05
I just upgraded a virtual machine from Fluxbuntu Hardy to Fluxbuntu Intrepid. I did this by editing /etc/apt/sources.list and changing all instances of hardy to intrepid, then sudo apt-get dist-upgrade.

The first problem I've run into is this. I can no longer run system tools such as synaptic using gksu. It brings up the Administrative Dialog box, which is new in Intrepid. I enter the correct password, but it tells me it's incorrect. After entering 3 "incorrect" passwords, I get the following error: 'Failed to run synaptic as user root. Wrong password.'

Interestingly, 'sudo synaptic' works okay.

---

### Post by Rocket2DMn on 2008-10-06
Moved to Intrepid Ibex Testing and Discussion.

---

### Post by inportb on 2008-10-06
Of course, sudo graphical-app *might* hijack some files required by Xorg. It's happened, so be careful.

---

### Post by snowpine on 2008-10-06
> **inportb said:**
> Of course, sudo graphical-app *might* hijack some files required by Xorg. It's happened, so be careful.

Yes, I would prefer to get gksu working correctly. Especially because it is one of the "exciting new features" of Intrepid. :)

---

