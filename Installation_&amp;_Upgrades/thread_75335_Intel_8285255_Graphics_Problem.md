---
title: "Intel 82852/55 Graphics Problem"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by zukakog on 2005-10-13
I have a Gateway m275 convertible laptop/tablet.  It has an "Intel 82852/82855 GM/GME Graphics Controller" according to Windows.

I've been successfully running 5.04 on it for quite a while.  Installation was a 'breeze' and it even setup OpenGL automatically.

I just wiped my old Hoary partition and did a fresh install of 5.10, (not so) Breezy Badger.

Everything installs smoothly, but when it's time to login, my screen is blank (off).  I see the nifty new brown progress bar saying that everything is starting, but when X actually starts, my monitor seems to shut off.  I hear the drums signaling me to log in, but I still can't see anything.

I've tried to <ctrl><alt>backspace to restart X, but get nothing.

I don't know how to get to any logs that would be helpful.

Any suggestions?

---

### Post by zukakog on 2005-12-30
I figured it out.  I had to add ```
Load     "i810"
``` to the Module section of /etc/X11/xorg.conf

---

