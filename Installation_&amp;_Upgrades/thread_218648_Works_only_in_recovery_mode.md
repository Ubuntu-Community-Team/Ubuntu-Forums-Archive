---
title: "Works only in recovery mode"
date: 2006-07-18
forum: Installation &amp; Upgrades
---

### Post by archmichael on 2006-07-18
I a noob who is at my wits end here.

Dapper freezes at or just before the x session starts. The live cd freezes before the session. Did a text install that went well, but it freezes aaat the login screen or sometimes just before.

When it freezes up, the keyboard dies. No NumLock or CapsLock light. The monitor still gets a signal.

I have a Radeon 9800Pro, and I have been trying all the ati driver fixes but nothing has worked.

The fact that I can 'startx' in recovery mode and it runs fine, leads me to believe it might be something other than the video driver but I don't know what.

---

### Post by taurus on 2006-07-18
Look in /etc/X11/xorg.conf to see which driver, Driver, do you have for your video card!  Try to use "vesa" instead!

---

### Post by archmichael on 2006-07-18
> **taurus said:**
> Look in /etc/X11/xorg.conf to see which driver, Driver, do you have for your video card!  Try to use "vesa" instead!
Forgot to mention that I tried this. Still hangs with 'vesa' instead of the default 'ati'. Tried changing it to 'radeon' as well as the numerous 'fglrx' fixes. Nothing works, but I can always startx in recovery mode.

Tried looking for errors in the xorg log, but there is nothing there.

---

### Post by archmichael on 2006-07-18
Found the source of the problem. It was my Logitech wireless trackball that was causing the entire system to hang

::shrugs::

---

