---
title: "(feisty) installer quits; even alternate reaches error"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by SoloSalsa on 2007-05-12
Hey!  Okay, I *want* to install Xubuntu 7.04 on a computer I built, never had an OS before.  I tried the Xubuntu graphical first, but installer just disappeared at like 22% or so of copying files.  Tried Ubuntu; same.  Tried Xubuntu 6.06: same (although the old installer did include a note).  Tried Xubuntu 7.04 alternate: SAME!  But, this is what I think is relevant of the syslog (the last few lines):
```
base-installer: error: exiting on error base-installer/kernel/failed-install
main-menu[3057]: WARNING **: Configuring 'base-installer' failed with error code 1
main-menu[3057]: WARNING **: Menu item 'base-installer' failed.
main-menu[3057]: INFO: Modifying debconf priority limit from 'high' to 'medium'
debconf: Setting debconf/priority to medium
main-menu[3057]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
main-menu[3057]: DEBUG: resolver (ext2-modules): package doesn't exist (ignored)
main-menu[3057]: DEBUG: resolver (firmware-modules): package doesn't exist (ignored)
main-menu[3057]: INFO: Falling back to the package description for console-setup-udeb
main-menu[3057]: INFO: Falling back to the package description for console-setup-udeb
main-menu[3057]: INFO: Menu item 'di-utils-shell' selected
```
Can anyone help?  I typed all that on a seperate machine (I did not know how to save it...); I did not copy the other lines.
Thanks.

---

### Post by gercokees on 2007-06-23
Hi,
I ran into the same problem, and posted my question here:
[http://forum.ubuntu-nl.org/topic/11970](http://forum.ubuntu-nl.org/topic/11970)

you might want to follow that one....
Greetz,

---

