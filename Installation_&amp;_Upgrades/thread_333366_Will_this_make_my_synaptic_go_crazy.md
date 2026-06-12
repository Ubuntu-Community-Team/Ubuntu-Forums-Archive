---
title: "Will this make my synaptic go crazy?"
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by Nonno Bassotto on 2007-01-07
EDIT: Don't care about the actual name of the packages if you don't know. The point here is the install procedure, so just  think of them as packages x, y, z...

I'm currently using TeTeX, but I'd like to change to TeXlive. The problem is that I'm also using the package Asymptote. This should be installable both on top of TeTeX or on top of TeXlive, but there is some bug that makes it depend only on TeTeX.

I found the following workaround.

If install TeXlive, synaptic forces me to remove TeTeX (correct), but also to remove Asymptote. Now if I mark Asymptote for a reinstall, Synaptic accepts it, but wants to remove Rubber. Finally I mark Rubber for reinstall and Synaptic asks me to mark TeXlive for install (which I already did). At this point the selection of package is correct.

Do you think that this will cause me problems when I install other packages or upgrade?

---

### Post by Nonno Bassotto on 2007-01-08
Bump

---

