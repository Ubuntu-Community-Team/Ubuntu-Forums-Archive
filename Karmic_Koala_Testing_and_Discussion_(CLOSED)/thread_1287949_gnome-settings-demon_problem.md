---
title: "gnome-settings-demon problem"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Xamiga on 2009-10-10
Karmic, up to date yesterday am.

How do I go about finding the solution to this ongoing problem?

In .xsession-errors:

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_SOCKET=/tmp/keyring-GYop3L/socket
SSH_AUTH_SOCK=/tmp/keyring-GYop3L/socket.ssh
GNOME_KEYRING_PID=1636

(gnome-settings-daemon:1635): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

** (gnome-settings-daemon:1635): WARNING **: Connection failed, reconnecting...

** (gnome-settings-daemon:1635): WARNING **: Connection failed, reconnecting...

This continues forever.  Any idea what it wants to connect to?

---

### Post by crys on 2009-10-10
No idea, but I've got the same problem. Additionally, my cpu usage is up to 100% due to Xorg. Don't know, whether both issues are related.

---

### Post by dino99 on 2009-10-11
bug report filled some time ago

[https://bugs.launchpad.net/gstreamer/+bug/384439](https://bugs.launchpad.net/gstreamer/+bug/384439)

please, let them know that bug affect yourself too.

---

