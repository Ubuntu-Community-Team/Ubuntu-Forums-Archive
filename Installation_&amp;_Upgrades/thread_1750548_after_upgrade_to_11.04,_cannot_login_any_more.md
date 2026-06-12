---
title: "after upgrade to 11.04, cannot login any more"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by ulukay on 2011-05-05
i've created a completely new user, so config files for fluxbox/unity/gnome cannot be the problem.
when i try to login with this user in gdm, the screen goes black for a few seconds and gdm displays again.
tried:
- new user without any gnome/unity/fluxbox config
- tried "ubuntu", "ubuntu-classic", "ubuntu-classic without effects", and "ubuntu-classic safe mode"
- did aptitude purge gdm & installed it again
- nvidia module is loaded properly
- no errors in /var/log/Xorg.0.log
- login with NXCLIENT on this server works perfectly fine!!!!

```
~# cat /home/testuser-gnome/.xsession-errors
/etc/gdm/Xsession: Beginning session setup...
.: 2: Can't open /etc/init.d/msm_profile

```

dmesg shows no errors

here's some syslog output:
```
May  5 22:57:05 server gdm-simple-greeter[27313]: Gtk-WARNING: /build/buildd/gtk+2.0-2.24.4/gtk/gtkwidget.c:5687: widget not within a GtkWindow
May  5 22:57:05 server gdm-simple-greeter[27313]: WARNING: Unable to load CK history: no seat-id found
May  5 22:57:09 server gdm-session-worker[27314]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  5 22:57:15 server gdm-session-worker[27335]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May  5 22:57:17 server gdm-session-worker[27335]: pam_sm_authenticate: Called
May  5 22:57:17 server gdm-session-worker[27335]: pam_sm_authenticate: username = [testuser-gnome]
May  5 22:57:17 server snmpd[2490]: error on subcontainer 'ia_addr' insert (-1)
May  5 22:57:18 server acpid: client 26440[0:0] has disconnected
May  5 22:57:18 server acpid: client 26440[0:0] has disconnected
May  5 22:57:18 server acpid: client connected from 27382[0:0]
May  5 22:57:18 server acpid: 1 client rule loaded
May  5 22:57:19 server acpid: client connected from 27382[0:0]
May  5 22:57:19 server acpid: 1 client rule loaded
May  5 22:57:20 server gdm-simple-greeter[27425]: Gtk-WARNING: /build/buildd/gtk+2.0-2.24.4/gtk/gtkwidget.c:5687: widget not within a GtkWindow
May  5 22:57:20 sunnyserver gdm-simple-greeter[27425]: WARNING: Unable to load CK history: no seat-id found

```

- tried: nvidia drivers, tried nouveau, tried nv - same error on every driver

edit: installed kdm, used it, works.
so the bug must be related to gdm.
unfortunately using kdm is unacceptable since user switching is not supported.

---

### Post by ulukay on 2011-05-06
bump :)

---

### Post by ulukay on 2011-05-06
tried to update all gnome stuff to 3.0
didn't help

got the same error as this guy.
still no solution ...
[http://ubuntuforums.org/showthread.php?t=1738674](http://ubuntuforums.org/showthread.php?t=1738674)


May  6 15:21:40 server gdm-simple-greeter[6892]: Gtk-WARNING: /build/buildd/gtk+3.0-3.0.8/./gtk/gtkwidget.c:6786: widget not within a GtkWindow
May  6 15:21:40 server gdm-simple-greeter[6892]: Gtk-WARNING: gtk_widget_size_allocate(): attempt to allocate widget with width -47 and height -47
May  6 15:21:40 server gdm-simple-greeter[6892]: Gdk-WARNING: gdk_xsettings_watch_cb(): Couldn't find window to unwatch

---

### Post by ulukay on 2011-05-06
finally found the problem ...
deleted the /etc/X11/xinit directory

remade 2 empty dirs
mkdir -p /etc/X11/xinit/xinitrc.d
mkdir -p /etc/X11/xinit/xinput.d

it works now

---

### Post by Bo Fussing on 2011-05-13
@ulukay

Do you have gnupg-agent installed?

If so your problem may be related to [https://bugs.launchpad.net/ubuntu/+source/gnupg2/+bug/766574](https://bugs.launchpad.net/ubuntu/+source/gnupg2/+bug/766574)

Bo

---

