---
title: "[Fixed] Video &amp; Sound fail after kernel update on Inspiron 1501"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by Beanalby on 2008-05-15
Telling my story here in case it helps anybody else...

After applying the recent round of updates, after logging in I'd get a blank white screen.  I figured it was a 3D compiz problem, and I was able to log in to Failsafe Gnome and change the window manager to Metacity. Once I logged in, sounds wasn't working.

After a lot of jiggering, I discovered that booting with the "Ubuntu 8.04, kernel 2.6.24-16-generic" kernel instead of the default "Ubuntu 8.04, kernel 2.6.24-16-386", everything magically worked again.  No idea what's going on or what causes it, but it works.

This is a Dell Inspiron 1501 that had the 8.04 beta installed just before th efinal release, nothing customized.

---

