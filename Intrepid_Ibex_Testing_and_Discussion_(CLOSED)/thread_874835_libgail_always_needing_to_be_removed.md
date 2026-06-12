---
title: "libgail always needing to be removed"
date: 2008-07-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bpl07 on 2008-07-30
I'm going through and selectively upgrading packages from hardy to intrepid.  However, many of the applications, especially those related to gnome, want to remove libgail (libgail-common, libgail-dev, and libgail18 to be exact).  The list of "to be installed" packages don't look like anything that would definitively replace these, so I've been avoiding these upgrades.  How have those who have completely upgraded to intrepid alpha avoided this issue?

---

### Post by pressureman on 2008-07-31
I removed libgail as part of a dist-upgrade last week, when I upgraded from Hardy to Intrepid. I haven't noticed any il-effects as a result.

---

### Post by Neon Lights on 2008-07-31
Remove it. Gail was merged into GTK.

---

### Post by Foaming Draught on 2008-08-01
Gnome-main-menu, better known as the SLAB, requires libgail and libgail18.

I quite like the SLAB.

---

### Post by lithorus on 2008-08-01
> **Foaming Draught said:**
> Gnome-main-menu, better known as the SLAB, requires libgail and libgail18.

I quite like the SLAB.
Then it'll probably just need a re-build for Intrepid.

---

