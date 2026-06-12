---
title: "Ubuntu 6.10 Installation freeze"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by xbenes2 on 2007-01-16
When I try to install Ubuntu 6.10, the process freezes.
So I deleted the quiet option and got the information that the installation freezes **after** processing 

scripts/init-bottom   ok

I suspect my sata drives or Ati radeon graphic card (safe graphic mode didnot help)

---

### Post by Greg Brennan on 2007-02-23
I am getting the same problem.  The machine is a Dell Inspiron 6400 laptop.  I have a 6000 that is working fine on the same version.  I have disabled speedstep in the BIOS and that has not made a difference.  The machine does come up sometimes but when it freezes here I need to hit 'the button', ctrl-alt-delete is not detected.

Frustrating to find that init-bottom was an empty directory and not a script where I'd find the command that was failing.

---

