---
title: "Unable to launch keyboard shortcuts in Gnome"
date: 2009-08-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by phenest on 2009-08-14
I'm not able to launch keyboard shortcuts in Gnome. If anyone else is finding the same, I'll report a bug. However, I'm not getting any errors, not even an automated crash report.

---

### Post by taavikko on 2009-08-14
Like this?
```
[ 5447.324268] gnome-keybindin[4149]: segfault at 30 ip 00007f2ded75e669 sp 00007fff10e5b7c0 error 4 in libgtk-x11-2.0.so.0.1707.0[7f2ded51f000+44a000]
```

And
```
hp-dv5:~$ gnome-keybinding-properties 

(gnome-keybinding-properties:4163): Gtk-CRITICAL **: gtk_tree_store_get_value: assertion `VALID_ITER (iter, tree_store)' failed

(gnome-keybinding-properties:4163): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.21.4/gobject/gtype.c:3940: type id `0' is invalid

(gnome-keybinding-properties:4163): GLib-GObject-WARNING **: can't peek value table for type `<invalid>' which is not currently referenced
Segmentation fault (core dumped)

```

---

### Post by phenest on 2009-08-14
That's it. I have the same here.

---

### Post by taavikko on 2009-08-14
> **phenest said:**
> That's it. I have the same here.

Then just
```
ubuntu-bug gnome-control-center
```

And I'll confirm.

---

### Post by phenest on 2009-08-14
[Bug 413481]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/413481")

---

### Post by taavikko on 2009-08-14
> **phenest said:**
> [Bug 413481]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/413481")

Confirmed.

---

### Post by rajeev1204 on 2009-08-14
Hey phenest , i had opened a thread similar to this,but you said it works well for you.But i dont get any messages like yours.

[http://ubuntuforums.org/showthread.php?t=1236585](http://ubuntuforums.org/showthread.php?t=1236585)

What gives.

---

### Post by phenest on 2009-08-14
Because this has only just happened.

---

