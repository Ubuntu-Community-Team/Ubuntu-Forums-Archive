---
title: "When do we get Gnome beta?"
date: 2009-08-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by froggyswamp on 2009-08-21
Folks, any idea when the Ubuntu devs push Gnome 2.6.28 beta into Karmic?
Alt+F2 isn't working and I'm wondering if the beta fixed this bug.

Tried checking whether this keyboard binding is set at all, but when running gnome-keybinding-properties I get:
> 
(gnome-keybinding-properties:11276): Gtk-CRITICAL **: gtk_tree_store_get_value: assertion `VALID_ITER (iter, tree_store)' failed

(gnome-keybinding-properties:11276): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.21.4/gobject/gtype.c:3940: type id `0' is invalid

(gnome-keybinding-properties:11276): GLib-GObject-WARNING **: can't peek value table for type `<invalid>' which is not currently referenced
Segmentation fault


---

### Post by castrojo on 2009-08-21
Probably next week when/if seb128 comes back from vacation. :D

---

### Post by MacUntu on 2009-08-21
Developers shouldn't be allowed to go on vacation. :lolflag:

---

### Post by gnomeuser on 2009-08-21
> **whiprush said:**
> Probably next week when/if seb128 comes back from vacation. :D

Wait.. I always thought Seb fell into the Ingo Molnar cloning vat when he was little.

People strange things are brewing.

---

### Post by Regenweald on 2009-08-21
I always forget that the Gnome cycle is a full month ahead of Ubuntu. .28 is almost out. Poor Breakage, the guy never quite got a chance to get here.

---

### Post by VMC on 2009-08-21
[QUOTE=froggyswamp;7824312]Folks, any idea when the Ubuntu devs push Gnome 2.6.28 beta into Karmic?
Alt+F2 isn't working and I'm wondering if the beta fixed this bug.
/QUOTE]I don't have that bug. Strange because I have all the others. Alt+F2 works for me.

---

### Post by JohnJackson on 2009-08-21
We do have some of the beta already, evince for example is 2.27.90. It's not version 2.6.28 though like the kernel versioning.

---

### Post by taavikko on 2009-08-21
> **VMC said:**
> 
[QUOTE=froggyswamp;7824312]Folks, any idea when the Ubuntu devs push Gnome 2.6.28 beta into Karmic?
Alt+F2 isn't working and I'm wondering if the beta fixed this bug.
I don't have that bug. Strange because I have all the others. Alt+F2 works for me.[/QUOTE]

Set the panel background to solid color ;) and voilá, you're affected.

---

### Post by VMC on 2009-08-21
> **taavikko said:**
> Set the panel background to solid color ;) and voilá, you're affected.

It is solid and I'm not affected :)

---

### Post by godhika on 2009-08-21
> **taavikko said:**
> Set the panel background to solid color ;) and voilá, you're affected.
It is exactly the other way around: Set the panel background to transparent and then ALT-F2 stops working

---

### Post by scradock on 2009-08-21
> **godhika said:**
> It is exactly the other way around: Set the panel background to transparent and then ALT-F2 stops working
worse than that - set panel background to solid color, then whatever you do to the setting Alt-F2 doesn't work (maybe after reboot?)

---

### Post by froggyswamp on 2009-08-21
Thanks folks,
with non-transparent panels Alt-F2 works again! (though the nvidia update screwed my system, already reported on the forum in another thread).

---

