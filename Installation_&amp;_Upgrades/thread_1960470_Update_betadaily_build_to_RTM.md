---
title: "Update beta/daily build to RTM?"
date: 2012-04-17
forum: Installation &amp; Upgrades
---

### Post by ftornell on 2012-04-17
Hi guys,
Searched the site and found some info about the question but not all.

Running a few Laptops/Workstations on Ubuntu 12.04 Beta 1, 2 and some daily builds.

They all can be upgraded to RTM (the real release) by just using:
# sudo apt-get update, correct?

But is this a supported way of upgrading or does Canonical prefer us to do real re-installations? Seems many have issues with these kinds of upgrades but since it's offered it must be supported?

The answere will most likely be, don't run this in production environment...I know.

---

### Post by Mark Phelps on 2012-04-17
In THEORY, that should work out OK ...

But in practice, a clean-install tends to be the better solution in the long run.

While upgrades will replace old stuff and add new stuff, you can't rely on them to clean out old stuff that is no longer used.

It's just better to start out with a clean slate.

---

