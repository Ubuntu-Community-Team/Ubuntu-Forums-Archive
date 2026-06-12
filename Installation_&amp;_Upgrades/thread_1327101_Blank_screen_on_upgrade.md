---
title: "Blank screen on upgrade"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by motrax on 2009-11-15
I upgraded from 9.04 to 9.10. I had applied all the updates to 9.04 before starting the update process.

During the upgradation process I was asked if i wanted to keep the old copy of menu.lst and I did. This resulted in me loggin into kernel-28-16. But then I edited menu.lst and changed the entries to 30.15. 

But since then I am getting a blank screen on boot. I can here the gdm sound. If I enter my password the user login sound plays, but nothing is displayed.

Pressing cntl+alt+f2-6 doesn't drop me to the command line. The screen just stays blank.

Please help.

SOLVED - I edited the boot options. Added i915.modeset=0. Works perfectly :)

---

