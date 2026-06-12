---
title: "Can't start totem after faulty upgrade"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by aleksey.zalesov on 2010-03-25
Hello!

I started #aptitude safe-upgrade and switched to another user. Gdm showed the error  and hung down the system. So I did reboot.

After reboot if I start totem I see such a result:
```
$ totem
ImportError: No module named gobject

** (totem:1978): WARNING **: Could not import pygtk
ImportError: No module named pygtk
Segmentation fault
```The output of rhythmbox is similar:
```
$ rhythmbox
ImportError: No module named gobject

** (rhythmbox:2025): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:2025): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(rhythmbox:2025): Rhythmbox-WARNING **: Could not import pygtk
ImportError: No module named pygtk
Segmentation fault

```I tried to complete the upgrade with aptitude safe-upgrade, but it shows that all packages are up to date. I am afraid that some other packages are affected by this crash. How can I repair system?

---

### Post by mango42 on 2010-03-25
I have a similar problem since upgrading from 9.04 to 9.10 (i386 on a Thinkpad T43 laptop)

Totem, RhythmBox, CD/DVDCreator (Brasero?) and Banshee all fail to load or function, whereas VLC and Flash in A Browser and Opera 10 work fine.

```
$ totem
sys:1: Warning: g_param_spec_internal: assertion `(name[0] >= 'A' && name[0] <= 'Z') || (name[0] >= 'a' && name[0] <= 'z')' failed

ERROR: Caught a segmentation fault while loading plugin file:
/usr/lib/gstreamer-0.10/libgstfrei0r.so

Please either:
- remove it and restart.
- run with --gst-disable-segtrap and debug.
Error re-scanning registry , child terminated by signal

```

The exact same error comes up when running **Rhythmbox**, **Banshee** and **Brasero** from the command line, so it looks like **/usr/lib/gstreamer-0.10/libgstfrei0r.so** is the culprit but what to do about it? I have tried complete re-installation of these apps from Synaptic but there's no change for the better. Searching specifically for **libgstfrei0r** in Synaptic draws a blank...

---

### Post by aleksey.zalesov on 2010-03-26
I solved this problem. 
```
# aptitude reinstall python-gobject
```

New aptitude command is learned ;)

---

### Post by mango42 on 2010-05-10
FYI, I finally pinned the problem down to when I attempted to install **Openshot** - once *completely* removed, the media players sprang back into action.

---

