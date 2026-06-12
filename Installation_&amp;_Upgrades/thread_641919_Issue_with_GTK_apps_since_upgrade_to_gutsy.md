---
title: "Issue with GTK apps since upgrade to gutsy"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by timczer on 2007-12-16
I used the update manager to upgrade from feisty to gutsy.  Now I am having issues with several apps running, and they all seem to have some type of GTK related error.

The apps I have had issues with are envy, awn, restricted drivers manager, and software sources.

The errors they are throwing are:
Envy:
> Traceback (most recent call last)
File "/usr/share/envy/gtkenvy.py", line 13, in <module>
    import sys, vte, re, os
ImportError: could not import gtk


restricted manager:
> Traceback (most recent call last):
  File "/usr/bin/restricted-manager", line 40, in <module>
    from RestrictedManager.RestrictedManagerGtk import RestrictedManagerGtk as RestrictedManager
  File "/usr/lib/python2.5/site-packages/RestrictedManager/RestrictedManagerGtk.py", line 28, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents

software sources:
> Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 27, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents


Also, any changes I make to my sessions profile are gone the next time I restart ubuntu.

Any ideas on this would be greatly appreciated.

---

