---
title: "C++/Mex code slower after upgrade from 10.04 to 12.04"
date: 2012-09-20
forum: Installation &amp; Upgrades
---

### Post by cturnes on 2012-09-20
I've been running some experiments using C++ code for MATLAB (i.e., mex functions) for several months now on my desktop.  Yesterday I upgraded to 12.04 LTS from 10.04, and I've noticed that my code has significantly dropped in speed.  It now runs faster on my laptop, despite the hardware on the desktop being significantly better (same amount of RAM, but 3.16 GHz dual core vs. 2.4 GHz dual core).

I checked that this isn't a problem with the MATLAB installation; the performance gap between intensive MATLAB functions on the desktop vs. the laptop is the same as it was prior to the upgrade.  After re-compiling and running the code, though, my speed after upgrading to 12.04 dropped by a factor of 3.

Anyone have any ideas as to potential remedies?  This isn't necessarily a critical problem, but I'd love to get the old speed back if possible...

---

### Post by cturnes on 2012-09-20
Update:  I added the matlab-support package, but this seems to have no effect.

---

### Post by ggrekas on 2013-02-01
I have the same issue..did you find any solution?

thanks

---

