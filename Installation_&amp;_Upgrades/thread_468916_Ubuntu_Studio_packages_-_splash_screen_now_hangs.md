---
title: "Ubuntu Studio packages - splash screen now hangs"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by Morbett on 2007-06-09
I installed some common Ubuntu Studio packages just now, and now when I boot up I have two problems:

1) The GNOME splash screen hangs a bit after Nautilus boots up, so I still see it on the desktop.

2) I have no title bar (metacity) at all. 

Any ideas?

---

### Post by cstrippie on 2007-06-09
I'm running into the same thing - can be traced (in my case) to either the updated compiz bits from trevino's repo or Avant Window Navigator.  I've used AWN extensively in feisty and edgy, so I doubt it's at fault.  I'll likely try purging all my compiz stuff and not allowing updates from trevino.

(YMMV)

---

### Post by Morbett on 2007-06-09
Thanks.  I completely removed all compiz packages and everything is fine now.

I removed the AWN repositories too, because I no longer had AWN installed.

---

