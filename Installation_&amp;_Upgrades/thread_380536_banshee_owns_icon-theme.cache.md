---
title: "banshee owns icon-theme.cache?"
date: 2007-03-09
forum: Installation &amp; Upgrades
---

### Post by spanella47 on 2007-03-09
tried searching for this with no sucess.

getting this error when trying to compile my own rhythmbox and mail-notification.
```
(Reading database ... 192846 files and directories currently installed.)
Preparing to replace mail-notification 3.0.dfsg.1-3ubuntu8 (using .../mail-notif
ication_4.0-1_i386.deb) ...
Unpacking replacement mail-notification ...
dpkg: error processing /home/spanella47/Desktop/mail-notification-4.0/mail-notif
ication_4.0-1_i386.deb (--install):
 trying to overwrite `/usr/share/icons/hicolor/icon-theme.cache', which is also 
in package banshee
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/spanella47/Desktop/mail-notification-4.0/mail-notification_4.0-1_i386.deb

```

the version of banshee i have installed was also self-compiled.  why is an icon cache part of the banshee package?  how do i get around this?

---

