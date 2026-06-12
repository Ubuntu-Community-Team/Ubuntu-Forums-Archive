---
title: "Latest Xubuntu 12.04 updates broke XFCE"
date: 2016-02-15
forum: Installation &amp; Upgrades
---

### Post by SagaciousKJB on 2016-02-15
I am not sure what at all happened, I tried updating my software with the update manager and the next thing I know, XFCE was now broken. No windows have the window title nor a "X" or "-" set of window controls.  It won't show desktop icons or allow me to right click the desktop to bring up the menu, and when trying to look at the system settings several sections such as the Windowmanager will not show up.

I've tired completely purging xubuntu desktop and everything xfce4 I could find as well as reinstalling the xorg server. No luck, I even decided to do a distribution upgrade to 14.04 ( mistake ) and that didn't fix it either, I can't tell what is broken on this system to make xfce not work.

I'm installing gnome right now to see what issues it might have as well.  The rest of the system seems to be working okay on 14.04 except for some weird errors during boot...

```
eb 15 02:00:45 AMD kernel: [   40.862279] systemd-udevd[1008]: failed to execute '/lib/udev/socket:@/org/freedesktop/hal/udev_event' 'socket:@/org/freedesktop/
```

But as i said, that's only AFTER upgrading to 14.04, and XFCE was borked when I installed the latest updates to 12.04

Update:

I installed gnome and it seems to be functioning 100% properly. So it appears the issue is with xfce4... Is anyone else having problems with the latest in the software repositories?

Is there a way to install the release just prior to the last updated? See if maybe there's something in the new code causing it?

---

### Post by SagaciousKJB on 2016-02-15
Okay figured it out, for whatever reason after i updated the first time it messed up my session cache.  Deleting ~/.cache/sessions/ fixed the problem

---

