---
title: "update-manager not working: shows python module import errors"
date: 2010-07-20
forum: Installation &amp; Upgrades
---

### Post by mayankbhagya on 2010-07-20
I installed an application today, which required python3.1
After this, my update-manager doesn't work.
When I try running update-manager from console, it threw the following errors:

> Traceback (most recent call last):
  File "/usr/bin/update-manager", line 29, in <module>
    import gtk
  File "/usr/share/pyshared/gtk-2.0/gtk/__init__.py", line 30, in <module>
    import gobject as _gobject
  File "/usr/share/pyshared/gtk-2.0/gobject/__init__.py", line 26, in <module>
    from glib import spawn_async, idle_add, timeout_add, timeout_add_seconds, \
  File "/usr/share/pyshared/gtk-2.0/glib/__init__.py", line 22, in <module>
    from glib._glib import *
ImportError: No module named _glib

The file /usr/bin/python points to python2.6
When I run python2.6, 'import gobject' doesn't throw an error
When I run python3.1, 'import gobject' throws an error.

This means that somehow update-manager is trying to use python3.1
I am experiencing similar problems with gedit-latex-plugin

How do I ensure that update-manager and gedit use the proper version of python OR how do I get the dist-packages in python3.1?

---

