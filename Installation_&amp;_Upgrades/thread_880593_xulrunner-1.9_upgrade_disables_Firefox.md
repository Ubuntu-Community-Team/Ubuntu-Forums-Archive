---
title: "xulrunner-1.9 upgrade disables Firefox"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by DogBone2020 on 2008-08-05
I've seen a lot of recent threads about xulrunner-1.9 problems. Mine is that a recent upgrade has disabled Firefox, which I can't repair owing to dependency problems. It seems the root cause may be that "xulrunner-1.9 is not configured yet". I don't know how to resolve this. Any suggestions much appreciated!

Terminal output runs like this:
[INDENT]Setting up xulrunner-1.9 (1.9.0.1+build1+nobinonly-0ubuntu0.8.04.3) ...
/usr/lib/xulrunner-1.9.0.1/xulrunner-bin: error while loading shared libraries: /usr/lib/xulrunner-1.9.0.1/libmozjs.so: invalid ELF header
dpkg: error processing xulrunner-1.9 (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of firefox-3.0:
 firefox-3.0 depends on xulrunner-1.9 (>= 1.9.0.1); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing firefox-3.0 (--configure):
 dependency problems - leaving unconfigured[/INDENT]

---

### Post by Archmage on 2008-08-05
Are you using the proposed reprose that have the tendencie to give you broken pagages from time to time?

---

### Post by DogBone2020 on 2008-08-05
Tks! I'm not sure I properly understand the question, but for Package Manager my Software Sources are as follows:
Ubuntu software: main, universe, restricted & multiverse
Third Party software: packages.medibuntu.org/hardy free non-free
Updates: hardy-security & hardy-updates only

---

