---
title: "X will not start after upgrade to 15.10"
date: 2015-11-16
forum: Installation &amp; Upgrades
---

### Post by BruceG on 2015-11-16
After upgrading my laptop to Ubuntu Gnome to 15.10 wily werewolf, X will no longer start. All I get is 5 brief flickers to black. Boot up works properly, and I am able to log in (in text mode, of course) on another console and over SSH. The same problem happens if I type "systemctl restart gdm" from the console.

There are no errors in Xorg.0.log, it just indicates a successful shutdown. The system log shows this though:

Nov 16 08:52:32 ranger1 org.a11y.Bus[3733]: Activating service name='org.a11y.atspi.Registry'
Nov 16 08:52:32 ranger1 org.a11y.Bus[3733]: Successfully activated service 'org.a11y.atspi.Registry'
Nov 16 08:52:32 ranger1 org.a11y.atspi.Registry[3744]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Nov 16 08:52:32 ranger1 org.gnome.ScreenSaver[3733]: ** (gnome-screensaver:3755): WARNING **: Couldn't get presence status: The name
Nov 16 08:52:32 ranger1 gnome-session[3736]: gnome-session[3736]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Nov 16 08:52:32 ranger1 gnome-session[3736]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Nov 16 08:52:32 ranger1 org.gnome.ScreenSaver[3733]: (gnome-screensaver:3755): Gdk-WARNING **: gnome-screensaver: Fatal IO error 11 
Nov 16 08:52:32 ranger1 org.a11y.atspi.Registry[3744]: XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
Nov 16 08:52:32 ranger1 org.a11y.atspi.Registry[3744]: after 21 requests (21 known processed) with 0 events remaining.
Nov 16 08:52:32 ranger1 org.gtk.vfs.Daemon[3733]: A connection to the bus can't be made
Nov 16 08:52:32 ranger1 gdm-launch-environment][3723]: pam_unix(gdm-launch-environment:session): session closed for user gdm
Nov 16 08:52:32 ranger1 gdm[3529]: GdmDisplay: display lasted 1.089261 seconds
Nov 16 08:52:32 ranger1 gdm[3529]: Child process -3727 was already dead.



So, it looks like gnome-screensaver failed to start due to some dbus error, which caused gnome-session to bail out (and so gdm as well).

Any ideas how to resolve this?

---

### Post by Vladlenin5000 on 2015-11-16
Do you have nvidia or AMD graphics running with proprietary drivers before upgrading? If so this a typical symptom and may or may not be solve by purging and reinstalling those drivers.
The general rule is to revert back to open source drivers *before* upgrading.

---

### Post by BruceG on 2015-11-16
No, this is an Intel-only laptop with no proprietary GPU drivers.

---

