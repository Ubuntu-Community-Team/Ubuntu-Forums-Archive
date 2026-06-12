---
title: "Add/Remove program"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by vasimakhtar on 2006-06-18
Hi,
When I run Add/Remove programs, it starts but after finishing software list the window disappear. Also the same with Software Properties under the menu of System/Administration/Software properties.
I am using Ubuntu 6 dapper with dual boot on XP.
thanks

---

### Post by aysiu on 2006-06-18
What happens when you enter this command in the terminal? ```
gksudo gnome-app-install
```

---

### Post by ildella on 2006-06-19
I have a similar problema, Add/Remove does not start. On the terminal, I have this error:

Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 20, in ?
    from AppInstall.AppInstall import AppInstall
  File "/usr/lib/python2.4/site-packages/AppInstall/AppInstall.py", line 62, in ?
    from SoftwareProperties.aptsources import SourcesList, is_mirror

You can view my complete report here: 
[http://ubuntuforums.org/showthread.php?t=199252&highlight=gnome-app-install](http://ubuntuforums.org/showthread.php?t=199252&highlight=gnome-app-install)

---

