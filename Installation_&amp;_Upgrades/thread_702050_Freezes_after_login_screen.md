---
title: "Freezes after login screen"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by MrDavinator on 2008-02-19
I am currently not able to log into Ubuntu.  After trying to log in, the screen freezes with my mouse working, and a light brown background.  I am able to change my session and log into Gnome, Falsafe Gnome, and Failsafe Terminal.  I'm not able to try and fix my problems though, because it says I'm not the super-user.

I did run the auto-update feature before this happened, and it froze.  After restarting my computer this is what happened.  How can I troubleshoot this so I know what is corrupt, and how to fix that?

---

### Post by MrDavinator on 2008-02-19
Fixed.  I had to start in recovery mode... then use the command:
dpkg --configure -a

---

