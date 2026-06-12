---
title: "Update Manager updated itself out of business..."
date: 2011-11-22
forum: Installation &amp; Upgrades
---

### Post by mercgt73 on 2011-11-22
I just ran an update from Update Manager, and now Software Center and Update Manager won't run in Gnome.  I ran them in the terminal and get these errors for both:
```
(gksu:2046): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
```
I tried re-installing Software Center but get this:
```
The following packages have unmet dependencies:
 software-center : Depends: gir1.2-glib-2.0 (>= 1.31) but 1.30.0-0ubuntu2 is to be installed
E: Unable to correct problems, you have held broken packages.

```I cannot find gir1.2-glib-2.0 with a version higher than 1.30.x, seems it wants it to be atleast 1.31?

I know there is a way to "fix" packages, but not sure how to do that.  Any help is appreciated.

-Rusty

---

### Post by mercgt73 on 2011-11-22
haha, ok I fixed it.  

So, I ran sudo update-manager and it loaded.  I ran the update again, rebooted, and it works from the desktop now.

I don't know why, something to do with me giving up on Ubuntu Unity and using Gnome classic.  I'm still learning.  ](*,)

So how do I mark this Resolved? lol

---

### Post by Frogs Hair on 2011-11-22
Use the thread tools on the top right of the first post .

---

