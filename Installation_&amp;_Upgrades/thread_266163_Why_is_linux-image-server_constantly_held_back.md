---
title: "Why is linux-image-server constantly held back?"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by bailey_ca on 2006-09-26
Is this happening to anyone else? linux-image-server seems to have been replaced with linux-server, but every time I try to upgrade, aptitude whines that linux-image-server is being held back; yet I can't remove it, as linux-server depends on it.

Just when I thought I had apt all figured out! *mutter*

---

### Post by aysiu on 2006-09-26
*aptitude* is pretty smart about stuff (dependencies and whatnot).

Sometimes it thinks it's a lot smarter than it really is, though. If you have a package that keeps getting held back, just use *apt-get* for that package.

---

