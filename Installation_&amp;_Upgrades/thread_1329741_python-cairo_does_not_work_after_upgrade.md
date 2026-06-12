---
title: "python-cairo does not work after upgrade"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by shadowcaster00 on 2009-11-17
I've just upgraded from Intrepid to Karmic, everything works fine except python-cairo.  Running software requiring python-cairo, ccsm for example, results in the following import error.


```
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 32, in <module>
    import gtk
  File "/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.6/dist-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: No module named _cairo
```


I tried to run "import cairo" in python console, it didn't work, same import error.  However, if I run python2.5 instead of python(the default is python2.6), the error message become

```
Info: No sexy-python package found, don't worry it's optional.
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 99, in <module>
    import compizconfig
ImportError: No module named compizconfig
```

I have python-gtk2, python-cairo, and python-gobject installed.  And I've tried dpkg-reconfigure.

What is the problem and how do I deal with it?

Dimitri

---

### Post by shadowcaster00 on 2009-12-02
anyone?

---

