---
title: "Removing packages with dependencies?"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by tsr on 2007-01-27
Hi,

Ok, I messed up, I forgot the main password for the key-ring manager, so I'm thinking about removing (with --purge) the key-ring package and the gnome-netstatus-applet and then reinstall them.

Two things worries me with this:
1. will it actually work? (will the system forget about my passwords, etc)
2. since gnome-netstatus-applet is depended upon by ubuntu-desktop will this also remove everything that is considered as the basic desktop features of ubuntu (I think not but want to be sure)

/tsr

---

### Post by tkjacobsen on 2007-01-27
1. probably not. Removing software will not erase user settings.
2. Dependencies is not automatically uninstalled, unless you use apt-get autoremove (in edgy /feisty). Don't worry about that.

---

