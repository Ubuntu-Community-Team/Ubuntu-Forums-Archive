---
title: "how to create install cd that doesn't need network access?"
date: 2011-08-23
forum: Installation &amp; Upgrades
---

### Post by Daniel Ellard on 2011-08-23
I'm trying to create a 10.04.3 installcd with a specific set of packages: nothing obviously special about it, just ubuntu-desktop, a few devel tools, and with a pre-seed file that sets up a few non-default parameters.

Everything works exactly the way I want it to, except for one important detail: the install always pulls packages over the network (and possibly updates to the apt database--it's not always easy to tell, during the install, exactly what it's doing).  In any case, it stalls if the network goes away in the middle of the install, and since the install is intended for places with poor, intermittent network connectivity, so this is an issue for me.

I tried doing an install without any network connectivity, and it succeeded, so all the necessary packages are in the ISO.  It's only when the network is available that it tries to pull over something (possibly apt files, since that's where the process seems to hang for hours when there is a slow network).  So I can install from scratch in 10 minutes when the network is disabled and 2 hours when the network is enabled--and no other changes!

I don't care if the resulting ISO file doesn't fit on a CD (as long as it fits onto a DVD), but I want an ISO that doesn't insist on reaching out over the network during the install.  Any ideas?

Thanks.

---

### Post by steve11911 on 2011-08-24
You seem to have found a good solution to the issue-just turn off the net before installing-but I understand-there must be a way to: ...

Probably somewhere linked below...there is...:

If you ever need to update offline there is a section on that here:

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

============

There are lots of solid choices for making custom distros:


[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

[http://uck.sourceforge.net/](http://uck.sourceforge.net/)

[http://maketecheasier.com/build-your-own-ubuntu-based-distro-with-novo-builder/2010/07/02](http://maketecheasier.com/build-your-own-ubuntu-based-distro-with-novo-builder/2010/07/02)

[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

latest pdf book - Linux from scratch link:

[http://www.linuxfromscratch.org/lfs/downloads/stable/LFS-BOOK-6.8.pdf](http://www.linuxfromscratch.org/lfs/downloads/stable/LFS-BOOK-6.8.pdf)

[http://linuxcoe.sourceforge.net/](http://linuxcoe.sourceforge.net/)

[https://github.com/lumentica/reconstructor.engine](https://github.com/lumentica/reconstructor.engine)

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

