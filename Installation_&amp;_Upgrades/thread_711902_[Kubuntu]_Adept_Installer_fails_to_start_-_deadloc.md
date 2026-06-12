---
title: "[Kubuntu] Adept Installer fails to start - deadlock?"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by CrazyArcher on 2008-03-01
When I try to install stuff or get upgrades, Adept says that another installer in already running. It happens even after fresh reboot. I can install programs from concole with dpkg, however.
Possible reasons or solutions?

---

### Post by gadgets on 2008-03-01
just had the same problem and this fixed it.
from terminal run
Open KONSOLE and type in the following: sudo dpkg --configure -a

then try it again.

gadgets:)

---

### Post by CrazyArcher on 2008-03-04
Yep, it worked. Thanks! :)

---

