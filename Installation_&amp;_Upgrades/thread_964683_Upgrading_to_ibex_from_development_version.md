---
title: "Upgrading to ibex from development version"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by andreselsuave on 2008-10-31
Hi there

I'm running the development version of intrepid ibex with some major bugs and now I want to upgrade to the official release. My update  manager doesn't show anything new... (I've already set the distribution updates to normal). what can I do? Do I have to make a fresh new installation?

Thanks a lot

---

### Post by Partyboi2 on 2008-10-31
If you are current with all the updates then you are already running the final release.

---

### Post by master5o1 on 2008-10-31
I agree with Partyboi2.  But you could try opening update manager from the terminal/alt+F2 and using `update-manager -d` as the command to search for a dist. upgrade.

---

### Post by kszys on 2008-10-31
> **master5o1 said:**
> I agree with Partyboi2.  But you could try opening update manager from the terminal/alt+F2 and using `update-manager -d` as the command to search for a dist. upgrade.

I am in a simmilar situation (i.e., was running Intrepid for some time now), so I thought I would give it a try as well...

Funny thing, when I try to run "update-manager -d" on the terminal in GNOME, I get 

```
/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 44, in <module>
    gtk.init_check()
RuntimeError: could not open display
```

---

