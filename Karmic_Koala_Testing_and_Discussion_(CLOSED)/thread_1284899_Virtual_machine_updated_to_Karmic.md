---
title: "Virtual machine updated to Karmic"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Peter09 on 2009-10-07
I have recently updated a virtualmachine (Vbox) to karmic. I log into this machine remotely. All seems to be working, but I have a terrible font and cannot seem to get it right. I also have the following error messages in syslog.

> 7 11:09:47 RemoteVM rtkit-daemon[2151]: Sucessfully called chroot.
Oct  7 11:09:47 RemoteVM rtkit-daemon[2151]: Sucessfully dropped privileges.
Oct  7 11:09:47 RemoteVM rtkit-daemon[2151]: Sucessfully limited resources.
Oct  7 11:09:47 RemoteVM rtkit-daemon[2151]: Canary thread running.
Oct  7 11:09:47 RemoteVM rtkit-daemon[2151]: Failed to make ourselves RT: Invalid argument
Oct  7 11:09:47 RemoteVM rtkit-daemon[2151]: Watchdog thread running.
Oct  7 11:09:47 RemoteVM rtkit-daemon[2151]: Running.
Oct  7 11:09:49 RemoteVM rtkit-daemon[2151]: Failed to make ourselves RT: Invalid argument
Oct  7 11:09:49 RemoteVM rtkit-daemon[2151]: Failed to make ourselves RT: Invalid argument
Oct  7 11:09:49 RemoteVM rtkit-daemon[2151]: Failed to make ourselves RT: Invalid argument
Oct  7 11:09:49 RemoteVM rtkit-daemon[2151]: Failed to make ourselves RT: Invalid argument
Oct  7 11:09:49 RemoteVM rtkit-daemon[2151]: Failed to make ourselves RT: Invalid argument
Oct  7 11:09:49 RemoteVM rtkit-daemon[2151]: Failed to make ourselves RT: Invalid argument
Oct  7 11:09:49 RemoteVM rtkit-daemon[2151]: Failed to make ourselves RT: Invalid argument
Oct  7 11:09:49 RemoteVM rtkit-daemon[2151]: Failed to make ourselves RT: Invalid argument
Oct  7 11:09:49 RemoteVM rtkit-daemon[2151]: Failed to make ourselves RT: Invalid argument
Oct  7 11:09:49 RemoteVM rtkit-daemon[2151]: Failed to make ourselves RT: Invalid argument
Oct  7 11:09:49 RemoteVM rtkit-daemon[2151]: Failed to make ourselves RT: Invalid argument
Oct  7 11:09:49 RemoteVM pulseaudio[2149]: shm.c: shm_open() failed: Read-only file system
Oct  7 11:09:49 RemoteVM pulseaudio[2149]: core.c: failed to allocate shared memory pool. Falling back to a normal memory pool.
Oct  7 11:10:43 RemoteVM rtkit-daemon[2151]: Failed to make ourselves RT: Invalid argument
Oct  7 11:10:43 RemoteVM rtkit-daemon[2151]: Failed to make ourselves RT: Invalid argument
Oct  7 11:10:43 RemoteVM rtkit-daemon[2151]: Failed to make ourselves RT: Invalid argument
Oct  7 11:10:43 RemoteVM rtkit-daemon[2151]: Failed to make ourselves RT: Invalid argument
Oct  7 11:10:43 RemoteVM rtkit-daemon[2151]: Failed to make ourselves RT: Invalid argument
Oct  7 11:10:43 RemoteVM rtkit-daemon[2151]: Failed to make ourselves RT: Invalid argument
Oct  7 11:10:43 RemoteVM rtkit-daemon[2151]: Failed to make ourselves RT: Invalid argument
Oct  7 11:10:43 RemoteVM rtkit-daemon[2151]: Failed to make ourselves RT: Invalid argument
Oct  7 11:10:43 RemoteVM rtkit-daemon[2151]: Failed to make ourselves RT: Invalid argument
Oct  7 11:10:43 RemoteVM rtkit-daemon[2151]: Failed to make ourselves RT: Invalid argument
Oct  7 11:10:43 RemoteVM rtkit-daemon[2151]: Failed to make ourselves RT: Invalid argument
Oct  7 11:10:43 RemoteVM pulseaudio[4103]: shm.c: shm_open() failed: Read-only file system
Oct  7 11:10:43 RemoteVM pulseaudio[4103]: core.c: failed to allocate shared memory pool. Falling back to a normal memory pool.
Oct  7 11:10:44 RemoteVM gnome-session[3865]: WARNING: GSIdleMonitor: IDLETIME counter not found
Oct  7 11:10:44 RemoteVM gnome-session[3865]: devkit-power-gobject-WARNING: unhandled property 'IsPresent'
Oct  7 11:10:44 RemoteVM gnome-session[3865]: devkit-power-gobject-WARNING: unhandled property 'RecallNotice'
Oct  7 11:10:44 RemoteVM gnome-session[3865]: devkit-power-gobject-WARNING: unhandled property 'Percentage'
Oct  7 11:10:44 RemoteVM gnome-session[3865]: devkit-power-gobject-WARNING: unhandled property 'RecallVendor'
Oct  7 11:10:44 RemoteVM gnome-session[3865]: devkit-power-gobject-WARNING: unhandled property 'RecallUrl'
Oct  7 11:10:44 RemoteVM gnome-session[3865]: devkit-power-gobject-WARNING: unhandled property 'UpdateTime'
Oct  7 11:10:44 RemoteVM gnome-session[3865]: devkit-power-gobject-WARNING: unhandled property 'Type'
Oct  7 11:10:44 RemoteVM gnome-session[3865]: devkit-power-gobject-WARNING: unhandled property 'TimeToEmpty'
Oct  7 11:10:44 RemoteVM gnome-session[3865]: devkit-power-gobject-WARNING: unhandled property 'Online'
Oct  7 11:10:44 RemoteVM gnome-session[3865]: devkit-power-gobject-WARNING: unhandled property 'EnergyRate'
Oct  7 11:10:44 RemoteVM gnome-session[3865]: devkit-power-gobject-WARNING: unhandled property 'NativePath'
Oct  7 11:10:44 RemoteVM gnome-session[3865]: devkit-power-gobject-WARNING: unhandled property 'Model'
Oct  7 11:10:44 RemoteVM gnome-session[3865]: devkit-power-gobject-WARNING: unhandled property 'Serial'
Oct  7 11:10:44 RemoteVM gnome-session[3865]: devkit-power-gobject-WARNING: unhandled property 'HasStatistics'
Oct  7 11:10:44 RemoteVM gnome-session[3865]: devkit-power-gobject-WARNING: unhandled property 'EnergyFull'
Oct  7 11:10:44 RemoteVM gnome-session[3865]: devkit-power-gobject-WARNING: unhandled property 'HasHistory'
Oct  7 11:10:44 RemoteVM gnome-session[3865]: devkit-power-gobject-WARNING: unhandled property 'EnergyFullDesign'
Oct  7 11:10:44 RemoteVM gnome-session[3865]: devkit-power-gobject-WARNING: unhandled property 'Vendor'
Oct  7 11:10:44 RemoteVM gnome-session[3865]: devkit-power-gobject-WARNING: unhandled property 'PowerSupply'
Oct  7 11:10:44 RemoteVM gnome-session[3865]: devkit-power-gobject-WARNING: unhandled property 'State'
Oct  7 11:10:44 RemoteVM gnome-session[3865]: devkit-power-gobject-WARNING: unhandled property 'TimeToFull'
Oct  7 11:10:44 RemoteVM gnome-session[3865]: devkit-power-gobject-WARNING: unhandled property 'EnergyEmpty'
Oct  7 11:10:44 RemoteVM gnome-session[3865]: devkit-power-gobject-WARNING: unhandled property 'IsRechargeable'
Oct  7 11:10:44 RemoteVM gnome-session[3865]: devkit-power-gobject-WARNING: unhandled property 'Technology'
Oct  7 11:10:44 RemoteVM gnome-session[3865]: devkit-power-gobject-WARNING: unhandled property 'Energy'
Oct  7 11:10:44 RemoteVM gnome-session[3865]: devkit-power-gobject-WARNING: unhandled property 'Voltage'
Oct  7 11:10:44 RemoteVM gnome-session[3865]: devkit-power-gobject-WARNING: unhandled property 'Capacity'
Oct  7 11:10:50 RemoteVM pulseaudio[4103]: module-x11-xsmp.c: X11 session manager not running.
Oct  7 11:10:50 RemoteVM pulseaudio[4103]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Oct  7 11:11:00 RemoteVM gnome-session[3865]: devkit-power-gobject-WARNING: No 'daemon-version' property
Oct  7 11:11:00 RemoteVM gnome-session[3865]: devkit-power-gobject-WARNING: No 'daemon-version' property
Oct  7 11:11:36 RemoteVM kernel: [   12.873136] type=1505 audit(1254910155.655:20): operation="profile_replace" pid=655 name=/usr/lib/cups/backend/cups-pdf
Oct  7 11:11:36 RemoteVM kernel: [   12.873136] type=1505 audit(1254910155.655:21): operation="profile_replace" pid=655 name=/usr/sbin/cupsd
Oct  7 11:11:36 RemoteVM kernel: [   13.007427] type=1505 audit(1254910155.787:22): operation="profile_replace" pid=656 name=/usr/sbin/ntpd

Anyone any thoughts on this?

---

### Post by gnutered on 2009-10-13
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/406702](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/406702)

Tony

---

