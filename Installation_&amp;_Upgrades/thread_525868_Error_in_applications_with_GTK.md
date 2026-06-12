---
title: "Error in applications with GTK"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by disoul on 2007-08-14
Hello... I recently upgraded my edgy to feisty, there are some errors but everything is fixed now.
Btw, I did see the warning of update-manager to update my packages. I d try to open the update-manager, but nothing happened, and in a test on gnome-terminal:

```
$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 28, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 56, in <module>
    from gtk._lazyutils import LazyNamespace, LazyModule
ImportError: cannot import name LazyNamespace
```
```
$ automatix2
  File "/usr/bin/automatix.py", line 34, in <module>
    from resin_config import *
  File "/usr/lib/automatix2/resin_config.py", line 12, in <module>
    import gtk, gtk.glade
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 56, in <module>
    from gtk._lazyutils import LazyNamespace, LazyModule
ImportError: cannot import name LazyNamespace
```

How I fix this error? =(

---

