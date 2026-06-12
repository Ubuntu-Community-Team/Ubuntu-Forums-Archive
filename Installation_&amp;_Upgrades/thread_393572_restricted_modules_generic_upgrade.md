---
title: "restricted modules generic upgrade"
date: 2007-03-25
forum: Installation &amp; Upgrades
---

### Post by sagasha on 2007-03-25
I installed 7.04 (fresh install.) All is well except I have 1 upgrade showing but when I try to upgrade I get:
Linux-restricted-modules-generic    -   Broken (Upgrade)

Any ideas?

---

### Post by adam.tropics on 2007-03-26
I know there was a kernel upgrade today, which would have wanted to also update your restricted modules. Sadly they weren't actually available until later in the day (at least) for me. So, if you did the update, you would have been required to reboot (since it was a kernel upgrade). Once you did that, then you would have restricted module problems until you update them to match the new kernel. (although I don't know whether or not they would show up as broken, I thought they would just show as an update, but greyed out (in update manager)) Just do another update, and see if it fixes it, if not, in synaptic, there is a fix broken packages  function in the menus.

---

