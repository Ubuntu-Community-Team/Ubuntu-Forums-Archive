---
title: "VNC xvnc4viewer"
date: 2011-06-29
forum: Installation &amp; Upgrades
---

### Post by geidorei on 2011-06-29
Hi

Installed xvnc4viewer, after looking thru forum - was unable to get keyboard to work with vncviewer, and it kept hanging.

However, keyboard still wont work - have disabled compiz effects on client and server. 

Any help appreciated. Karl

---

### Post by howefield on 2011-06-29
Try checking off the xdamage option in the machine you are trying to connect to.

Press the ALT + F2 keys and type

```
gconf-editor
```

Navigate to desktop > gnome > remote_access > disable_xdamage and tick the box. Close out and reboot, then try VNC again ?

If it doesn't work, then easy enough to reverse and uncheck.

---

### Post by geidorei on 2011-06-29
Hi - many thanks for info - didnt make any difference Im afraid. Any other suggestions?

Or is this a bug that seams to have been going on for ages?

---

### Post by geidorei on 2011-06-29
Hi - found problem - dont run with option 'fullscreen' - then it works.

Joy, another bug. lol

---

