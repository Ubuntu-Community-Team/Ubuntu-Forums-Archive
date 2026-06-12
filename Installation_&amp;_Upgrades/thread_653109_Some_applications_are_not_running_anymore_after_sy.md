---
title: "Some applications are not running anymore after system-update"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by Steffen_77 on 2007-12-29
I just got my new laptop and did a completely new installation of Ubuntu 7.10. Everything is working fine, but when I accept to update the system with the 148 (or so) available new packages I cannot run most of the applications (e.g. Terminal, OpenOffice, Pidgin, ...) anymore. When I start an application the startup process takes quite a while (the message "Starting up ..." is displayed) and then just stopps without any further notification. Any idea what could be wrong here? Or how to determine the problem?

Thanks in advance for any kind of support,
-Steffen-

Update:
This is what I have in the file ~/.xsession.errors, don't know if this could be related to the problems I am facing:

Segmentation fault
Segmentation fault
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/steffen-ubuntu:/tmp/.ICE-unix/5739
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Failed to read saved session file /home/steffen/.metacity/sessions/default0.ms: Failed to open file '/home/steffen/.metacity/sessions/default0.ms': No such file or directory
** Message: Not starting remote desktop server


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
Throttle level is 0
evolution-alarm-notify-Message: Setting timeout for 28712 1198972800 1198944088
evolution-alarm-notify-Message:  Sun Dec 30 01:00:00 2007

evolution-alarm-notify-Message:  Sat Dec 29 17:01:28 2007

Initializing gnome-mount extension

** (nm-applet:5856): WARNING **: <WARN>  nma_dbus_device_properties_cb(): dbus returned an error.
  (org.freedesktop.NetworkManager.DeviceNotFound) The requested network device does not exist.



** (nm-applet:5856): WARNING **: <WARN>  nma_dbus_device_properties_cb(): dbus returned an error.
  (org.freedesktop.NetworkManager.DeviceNotFound) The requested network device does not exist.



** (update-notifier:5844): WARNING **: no cdrom: disk

---

