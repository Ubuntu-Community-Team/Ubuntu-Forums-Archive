---
title: "KDE notifications broken - yellow popups"
date: 2009-09-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by timas on 2009-09-21
I've been having this problem since somewhere late in Jaunty. I recently updated to Karmic in an attempt to fix it, but no luck.

My libnotify notifications are yellow bubbles, I think gtk style. They should be KDE4 toaster style popups. See [http://www.box.net/shared/mpsz83zm3c](http://www.box.net/shared/mpsz83zm3c) for the broken version.

I would really like to be able to fix this, because I've been staring at these gimp notifications for far too long now :(

I believe I've drained every resource, search option, idea and fix I can think off in order to try and get this fixed.. I really just have no idea where to look.

The weirdest part to me is that file transfer type popups are the proper KDE4 style ones.

Any ideas?

---

### Post by Zorael on 2009-09-21
What if you removed notification-daemon and notify-osd? Does it threaten with removing a whole slew of other apps?
```
$ sudo aptitude purge notification-daemon notify-osd
```

---

### Post by timas on 2009-09-22
Wooo! I believe that fixed it!

Thank you /so/ much!

---

