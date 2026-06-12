---
title: "something tries to start metacity with a wrong parameter"
date: 2009-07-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by wayne_cat on 2009-07-25
I get this:

```
root@macbook:~$ ps ax |grep meta
 4705 tty1     S      0:00 /usr/bin/metacity --replace --replace
 4833 ?        S      0:00 /usr/lib/gvfs/gvfsd-metadata
 6069 tty1     R      0:00 metacity
 6081 pts/0    R+     0:00 grep meta
root@macbook:~$

```if I start Gnome with startx ... metacity with 2x "--replace"

The result: high CPU usage and a lot of errors in .xsession-errors:


```
Window manager warning: Screen 0 on display ":0.0" already has a window manager; 
try using the --replace option to replace the current window manager.

```Any idea what tries to start metacity this way?

---

### Post by wayne_cat on 2009-07-25
have found it ... known problem

[https://bugs.launchpad.net/metacity/+bug/389686](https://bugs.launchpad.net/metacity/+bug/389686)

---

