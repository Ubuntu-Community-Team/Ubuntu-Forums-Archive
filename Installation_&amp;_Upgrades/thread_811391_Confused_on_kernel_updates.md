---
title: "Confused on kernel updates"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by Wee Aldo on 2008-05-29
Hello all....

My problem is that I have compiled my sound card driver (SB X-FI) against a particular kernel <I can't immediately remember which one), downloaded the source etc, when a new kernel update is issued from automatic updates do I have to recompile against the new kernel to keep using my sound card?, and keep doing so as new kernel updates are released? I realize if I press the esc key I can choose from previous kernel installations, but that means I am forced to use an out of date kernel, with the obvious and attendant bug and security issues.

Thanks in advance

---

### Post by sdennie on 2008-05-29
Yes.  Any "driver" (kernel module) will be kernel specific and so you'll have to rebuild it whenever a largish kernel change comes out (specifically, when the -XX number changes).  I don't think this usually happens very often though.

---

