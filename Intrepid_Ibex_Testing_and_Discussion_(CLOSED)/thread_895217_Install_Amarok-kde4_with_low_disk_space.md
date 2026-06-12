---
title: "Install Amarok-kde4 with low disk space"
date: 2008-08-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by TheMono on 2008-08-20
OK... Before I say this, my first comment is, DON'T DO THIS if you can possibly avoid it.

I'm testing Intrepid on an EEEPC, so I have very limited HDD space. This of course means I can't run Amarok-kde4, as it depends on every debugging library under the sun - a total of over 500MB of disk space needed.

So... I build a dummy package to fill the debug dependencies. Now, as I said at the start, if you have the space, do install the debugging symbols. however, if you don't have the space, then this beats not running it at all.

Download and install the attached package to fill the libqt4-dbg, kdelibs5-dbg and amarok-kde4-dbg dependencies.

I repeat, don't do this unless you really have to, and you know what you're doing.

---

