---
title: "Lucid-&gt;Maverick login screen GDM failure"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by klotz on 2010-10-11
I upgraded from Lucid to Maverick.  The GDM login screen presents no usernames.  I couldn't log in.  

Below are symptoms and the workaround I did, which is probably incorrect.  However, after the workarounds, I could log in.

[SIZE="2"]Suspicious log entry #1[/SIZE]
/var/log/gdm/:0-slave.log says
[INDENT](gnome-power-manager:1082): libupower-glib-WARNING **: Couldn't enumerate devices: Failed to execute program /lib/dbus-1.0/dbus-daemon-launch-helper
: Success
*** ERROR ***
TI:16:08:06	TH:0x8e208b8	FI:gpm-engine.c	FN:gpm_engine_coldplug_idle_cb,837
 - failed to get device list: Failed to execute program /lib/dbus-1.0/dbus-daemon-launch-helper: Success
Traceback:
	gnome-power-manager() [0x806274b]
	gnome-power-manager() [0x8060f38]
	/lib/libglib-2.0.so.0(+0x3b841) [0x45f841]
	/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1d5) [0x461855]
	/lib/libglib-2.0.so.0(+0x41668) [0x465668]
	/lib/libglib-2.0.so.0(g_main_loop_run+0x187) [0x465ba7]
	gnome-power-manager() [0x805609a]
	/lib/libc.so.6(__libc_start_main+0xe7) [0x957ce7]
	gnome-power-manager() [0x804dc91]
gdm-simple-greeter[1079]: Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow[/INDENT]

I see some bugs in Fedora about permissions with this file but they claim it's OK in Ubuntu: [https://bugzilla.redhat.com/show_bug.cgi?id=607715](https://bugzilla.redhat.com/show_bug.cgi?id=607715)

I checked permissions:
[INDENT]ls -l /lib/dbus-1.0/dbus-daemon-launch-helper
-rwsr--r-- 1 root messagebus ... /lib/dbus-1.0/dbus-daemon-launch-helper
[/INDENT]

Workaround:
[INDENT]I did chmod a+x /lib/dbus-1.0/dbus-daemon-launch-helper
[/INDENT]



[SIZE="2"]Suspicious log entry #2:[/SIZE]
/var/run/daemon.log says
[INDENT]daemon.log:Oct 11 16:05:54 klotzpc console-kit-daemon[3945]: DEBUG: Couldn't open directory /var/run/console: Error opening directory '/var/run/console': No such file or directory
[/INDENT]


[SIZE="2"]Workaround:[/SIZE]
I did
[INDENT]mkdir /var/run/console
[/INDENT]

---

