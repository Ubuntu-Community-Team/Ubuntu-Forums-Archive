---
title: "Run live CD/DVD Toshiba C660 - blank screen"
date: 2011-03-19
forum: Installation &amp; Upgrades
---

### Post by madwoollything on 2011-03-19
I've been trying for some time to install Ubuntu 10.10 or variant on my Toshiba C660 with ATI graphics card.

I seem to keep hitting a brick wall when attempting to run a live disc and end up at a blank screen. I get this result despite trying lots of different installation discs. Ubuntu 10.04 seems to run with no problems.

I believe the problem is to do with the graphics card from googling and have tried various changes to the live cd/dvd boot options (set nomodeset & radeon.modeset=0) but with no success.

Any suggestions??

---

### Post by madwoollything on 2011-04-23
Sorted ...... found this post about another C660 and it works. [http://ubuntuforums.org/showthread.php?p=10709393#post10709393](http://ubuntuforums.org/showthread.php?p=10709393#post10709393)

In the cmos menu (press F2 before boot), under the Advanced Tab there is a setting called USB Legacy Emulation. If this is set to 'Enabled' the white flashing cursor as described will flash for ever. If set to 'Disabled' Ubuntu fires up ok. 100% repeatable

---

