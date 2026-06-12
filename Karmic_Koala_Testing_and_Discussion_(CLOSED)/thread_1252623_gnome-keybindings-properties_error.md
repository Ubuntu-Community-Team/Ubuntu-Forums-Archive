---
title: "gnome-keybindings-properties error"
date: 2009-08-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Paqman on 2009-08-29
Anybody else seeing this when trying to launch gnome-keybinding-properties?
```
(gnome-keybinding-properties:12427): Gtk-CRITICAL **: gtk_tree_store_get_value: assertion `VALID_ITER (iter, tree_store)' failed

(gnome-keybinding-properties:12427): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.21.5/gobject/gtype.c:3940: type id `0' is invalid

(gnome-keybinding-properties:12427): GLib-GObject-WARNING **: can't peek value table for type `<invalid>' which is not currently referenced
Segmentation fault (core dumped)

```

---

### Post by taavikko on 2009-08-29
[https://bugs.edge.launchpad.net/ubuntu/+source/gnome-control-center/+bug/412732](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-control-center/+bug/412732)

---

### Post by Paqman on 2009-08-29
Hmmm, -10 search points for Paqman then...

---

### Post by taavikko on 2009-08-29
> **Paqman said:**
> Hmmm, -10 search points for Paqman then...

+11 points for recognizing own flaws :)
So ending up ahead.

---

### Post by Paqman on 2009-08-29
Woot! :P

---

