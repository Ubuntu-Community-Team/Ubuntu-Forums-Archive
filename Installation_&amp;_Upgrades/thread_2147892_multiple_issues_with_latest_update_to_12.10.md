---
title: "multiple issues with latest update to 12.10"
date: 2013-05-23
forum: Installation &amp; Upgrades
---

### Post by jbeiter on 2013-05-23
Just a warning, I've had several headaches with the last update to 12.10.

Wondering if anyone knows how to address this one without breaking other stuff.  After updating, I can't run nxserver any more:

/etc/init.d/nxserver restart
Trying to restart NX server:
/usr/NX/bin/nxserver: error while loading shared libraries: /usr/NX/lib/perl/IO.so: wrong ELF class: ELFCLASS64
Trying to restart NX statistics:
/usr/NX/bin/nxserver: error while loading shared libraries: /usr/NX/lib/perl/IO.so: wrong ELF class: ELFCLASS64

---

### Post by dino99 on 2013-05-23
looks like conflicts with libraries : check that nxserver is for 12.10
[https://launchpad.net/~elquike/+archive/ppa](https://launchpad.net/~elquike/+archive/ppa)

---

### Post by jbeiter on 2013-05-23
Its been running fine for over 6 months, until yesterday.   Suspecting ubuntu boogered up something with libraries, I tried installing the 64bit version, but the old one refuses to un-install with the same error.

Not seeing a clean way to rip this out, or fix.  Much grief with this update.

---

