---
title: "About new dbus update."
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Vanishing on 2009-10-01
I saw that karmic beta is officially out, but there is still a hold up of a dbus update(or is it me?). I had it since yesterday, it is a dependency issue, which involves with upstart.
Is this only happening to me? I thought it was gonna be solved when beta comes out.:(
Hope noone opened a thread about this yet, otherwise I'm just repeating.

Thank you!

---

### Post by Amaranth on 2009-10-01
You're using the ubuntu-boot PPA. They uploaded a dbus to it that depends on a -6 upstart but the upstart available is -6~boot1 (which is lower due to how the ~ is handled).

---

