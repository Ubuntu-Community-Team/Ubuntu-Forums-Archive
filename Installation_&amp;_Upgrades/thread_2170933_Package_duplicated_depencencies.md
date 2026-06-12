---
title: "Package duplicated depencencies"
date: 2013-08-28
forum: Installation &amp; Upgrades
---

### Post by garejnc on 2013-08-28
In Gimp ppa there is are dependancies to gimp package and two of those are:
gimp-data (>= 2.8.6), gimp-data (<= 2.8.6-z)

but only one package gimp-data. 
I am interested why is that so and is that common?
I am trying to build an application and that would be a part of it.

Thanks.

---

### Post by tgalati4 on 2013-08-28
Don't know about gimp specifically, but usually these double dependencies are done as a transition to a different library structure.  One is probably a dummy dependency.  When code is in development (as PPA code tends to be) it gets refactored--pulled apart, rewritten, and put back together again.  When it is reassembled, some dependencies are dropped, others are added, some are merged.  So dummy packages are used to satisfy dependencies to allow building until the transition is done.

Of course it could simply be a packaging error.

If you are writing a gimp plug-in, why can't you target the stable version?

---

