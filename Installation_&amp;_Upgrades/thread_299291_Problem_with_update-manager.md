---
title: "Problem with update-manager"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by venesite on 2006-11-13
In the update of Drapper to Edgy I had a problem when finalizing the update because the package **spampd** did not stop and cancelled unexpectedly.

Nevertheless I have been able to recover the system and works, but when trying to execute: update-manager it appears the following error:

sudo update-manager
warning: could not initiate dbus
/usr/lib/python2.4/site-packages/DistUpgrade/DistUpgradeViewGtk.py:351: GtkWarning: gdk_gc_get_colormap: assertion `GDK_IS_GC (gc)' failed
  self._term.realize()

Somebody could help me. Thank you very much.

---

