---
title: "[SOLVED] Programs auto close after gutsy upgrade"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by nrune on 2007-10-20
Toshiba laptop a15-s129 
Running 7.04 updated to 7.10 yesterday

The following programs run and obviously instantly close or do not run at all:
Terminal; Restricted Drivers, advanced desktop settings, upgrade manager and more

I installed KDE to run Konsole:
```
nrune@nrune-laptop:/usr/bin$ sudo restricted-manager
[sudo] password for nrune:
Traceback (most recent call last):
  File "/usr/bin/restricted-manager", line 40, in <module>
    from RestrictedManager.RestrictedManagerGtk import RestrictedManagerGtk as RestrictedManager
  File "/usr/lib/python2.5/site-packages/RestrictedManager/RestrictedManagerGtk.py", line 28, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents
nrune@nrune-laptop:/usr/bin$ gksu "update-manager -c"
  File "/usr/bin/update-manager", line 28, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents

```

The terminal output for gnome-terminal is diffrent;
```
nrune@nrune-laptop:/usr/bin$ gnome-terminal
The program 'gnome-terminal' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 979 error_code 8 request_code 72 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

Can I buy a clue for a dollar? 

Thanks
Mike

---

### Post by nrune on 2007-10-21
Okay some further information. 

I can get gnome-terminal to run when I am using Konsole and do a sudo -s to become root. 

Nothing else works but perhaps there might be a clue there for someone to help. 

```
nrune@nrune-laptop:~$ sudo -s
root@nrune-laptop:~# gnome-terminal
root@nrune-laptop:~# restricted-manager
Traceback (most recent call last):
  File "/usr/bin/restricted-manager", line 40, in <module>
    from RestrictedManager.RestrictedManagerGtk import RestrictedManagerGtk as RestrictedManager
  File "/usr/lib/python2.5/site-packages/RestrictedManager/RestrictedManagerGtk.py", line 28, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents
```

---

### Post by nrune on 2007-10-23
Okay I gave up and did a total new install.  Probably was time for one any way.  Now that it is running properly, wow is gutsy cool.  Thanks all

Mike

---

