---
title: "Python modules fail in Terminal"
date: 2012-01-09
forum: Installation &amp; Upgrades
---

### Post by uzr on 2012-01-09
Hi guys.

Here is my problem

```


help> modules

Please wait a moment while I gather a list of all available modules...

/usr/lib/python2.7/dist-packages/gobject/constants.py:24: Warning: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
  import gobject._gobject
/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:40: Warning: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
  from gtk import _gtk

** (python:26115): CRITICAL **: pyg_register_boxed: assertion `boxed_type != 0' failed
/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:40: Warning: cannot register existing type `GdkDevice'
  from gtk import _gtk
/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:40: Warning: g_type_get_qdata: assertion `node != NULL' failed
  from gtk import _gtk
Segmentation fault


```What's the problem here?

---

### Post by dino99 on 2012-01-09
report this issue on Launchpad (need an user account)

in a terminal:

ubuntu-bug python

---

### Post by fluteflute on 2012-07-02
[https://bugs.launchpad.net/ubuntu/+source/python2.7/+bug/896836](https://bugs.launchpad.net/ubuntu/+source/python2.7/+bug/896836)

---

