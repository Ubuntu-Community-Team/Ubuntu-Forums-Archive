---
title: "How to get the ATI Driver working in 10.10"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by koblin3426 on 2010-10-21
If you had an issue installing the additional driver for an ATI card or enabling compiz desktop effects in 10.10, here's how to fix it!  I figured I had to wait until ATI came out with the proper driver but I guess they (or ubuntu?) actually have a driver that works correctly in 10.10.  It's just that in my case (and others as there's another thread about this), they didn't install the way they're supposed to.  So, here's how you can easily fix the issue:

1. Open synaptic and search for "FG". Reinstall all of the listed installed packages, and make sure you upgrade all packages that say jockey too which should show an exclamation point next to it (right click ---> upgrade). Click apply.

2. Then, search synaptic for "Compiz" and reinstall all packages (and install extra plugins if you want fire! ).

3. Then reboot and it SHOULD work. At least, that's how I fixed it.

NOTE: I imagine that you don't actually have to reinstall the packages for fgrlx. You most likely only have to "upgrade" those two Jockey packages with the exclamation point. Not sure as I am an Ubuntu novice.

:popcorn:

---

