---
title: "Gimp is crashing repeatedly"
date: 2009-02-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tawmas on 2009-02-22
So, I've had this for a 3 or 4 days now and I'm wondering if anybody else has the same.

Right now, I can't use the Gimp, except for very very quick edits, because it crashes all the times. Crashes appear to be random: they usually happen while I'm using the menu (just browsing through the menu, not executing a menu command) or while it's just sitting there with one or two images open.

I'm not doing anything memory- or cpu-intensive, so that baffles me.

Apport does not kick in, so I guess my next step will be to attach a debugger and see if I get some useful data for a bug report.

---

### Post by rockorequin on 2009-03-03
It crashes all the time on my Jaunty as well. There's a bug for it - [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/330846](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/330846) - which has been lodged upstream as well at [http://bugzilla.gnome.org/show_bug.cgi?id=572403](http://bugzilla.gnome.org/show_bug.cgi?id=572403).

---

### Post by afv on 2009-04-14
GIMP won't start for me (since about one week ago):

> 
*me@computer:~$ gimp*

(gimp:12042): GLib-GObject-WARNING **: specified class size for type `GimpOperationPointFilter' is smaller than the parent type's `GeglOperationPointFilter' class size

(gimp:12042): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gimp:12042): GLib-GObject-CRITICAL **: g_type_register_static: assertion `parent_type > 0' failed

(gimp:12042): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gimp:12042): GLib-GObject-WARNING **: cannot retrieve class for invalid (unclassed) type `<invalid>'


---

### Post by oberonking on 2009-04-22
> **afv said:**
> GIMP won't start for me (since about one week ago):

Same here... exactly the same error.

```
(gimp:4200): GLib-GObject-WARNING **: specified class size for type `GimpOperationPointFilter' is smaller than the parent type's `GeglOperationPointFilter' class size

(gimp:4200): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gimp:4200): GLib-GObject-CRITICAL **: g_type_register_static: assertion `parent_type > 0' failed

(gimp:4200): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gimp:4200): GLib-GObject-WARNING **: cannot retrieve class for invalid (unclassed) type `<invalid>'

```

Any idea??

---

