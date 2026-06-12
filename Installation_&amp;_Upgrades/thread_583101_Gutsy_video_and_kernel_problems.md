---
title: "Gutsy video and kernel problems"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by waltervalderrama on 2007-10-20
Hello guys, I've recently upgraded to gutsy, but I have the following problems:

- I cannot open "Restricted Drivers" utility, i don't know if the application is missing.
- I cannot open "update-manager" too. When I type the command I get the following: 

andre1@valderrama:~$ update-manager 
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 28, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents

I don't know if this is related to graphics, I think so.

---

### Post by nrune on 2007-10-21
If it helps, your not alone, there are about four threads going all with the same issue. No solution that I have found yet.  

my thread:
[http://ubuntuforums.org/showthread.php?t=584364](http://ubuntuforums.org/showthread.php?t=584364)

Mike

---

