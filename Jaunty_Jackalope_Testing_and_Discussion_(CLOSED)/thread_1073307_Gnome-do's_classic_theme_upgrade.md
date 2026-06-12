---
title: "Gnome-do's classic theme upgrade"
date: 2009-02-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by OliW on 2009-02-18
I was just playing around with gnome-do's theme selection and noticed that if you open preferences and close them again, you get a super-sexy-happy-time upgrade to the classic theme (as documented in my screenshots).

After restarting it reverts to the odler version. Question is, why isn't this enabled by default? The design and animations are beautiful!

---

### Post by kurros on 2009-02-18
Did you not have composting enabled when launching gnome-do? Otherwise it only checks for a compositer when opening the preferences window.

---

### Post by OliW on 2009-02-18
Ah! Yes compiz crashes (or otherwise fails to load) on boot. I need to start it manually and by that time g-d has loaded. Thanks for the explanation!

---

### Post by kurros on 2009-02-18
Ah. that must be annoying. There is a [todo bug]("https://bugs.launchpad.net/do/+bug/321742") open to have gnome-do detect via Gdk when compositing is enabled/disabled.

---

