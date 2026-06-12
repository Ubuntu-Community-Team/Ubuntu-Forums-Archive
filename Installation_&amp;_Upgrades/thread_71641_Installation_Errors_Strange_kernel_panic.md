---
title: "Installation Errors: Strange kernel panic"
date: 2005-10-03
forum: Installation &amp; Upgrades
---

### Post by illusina on 2005-10-03
Hello everyone,
Just installed ubuntu 5.04 amd64, when my system froze up. this has happened before in i386, so I tried amd64 to no avail. I rebooted (manual reset, completely frozen system), then ran into a "packages didn't properly install" page, which sent me to the apt front-end. I quit that, then it froze with a blank screen again. Rebooted yet another time, then was greeted by the following message right after the "package installation errors" page came up:
code:
<0> Kernel Panic - not syncing: Aiee, killing interrupt handler.
My specs are:
K8T800 motherboard
AMD 64 2800+
1GB DDR RAM
Radeon 9200 Sapphire
If there's any other information you guys need regarding my specs I'll try to get that for you..:) 
Regards,

---

### Post by illusina on 2005-10-04
Hello everyone,

Well I booted in again, and I think I'm pass that strange kernel panic. Anyways, when I try to re-install/fix my x11 packages (which I think is where the problem lies), I get the a system freeze on running dpkg --configure -a, and it freezes on the xserver-xorg (6.8.2-10) package. I'm knew to apt and dpkg, so I don't quite know how to proceed from here, given that I had other problems as well (I might need to find another distro as this distro doesn't seem to like my hardware :D).

Regards,

---

### Post by darkmatter on 2005-10-04
what exactly is the error you are getting in regards to the xserver? Is it configured at all, or is it just incorrectly configured?

If it is incorrectly configured, run

```
dpkg-reconfigure xserver-xorg
```

from the root prompt.

---

