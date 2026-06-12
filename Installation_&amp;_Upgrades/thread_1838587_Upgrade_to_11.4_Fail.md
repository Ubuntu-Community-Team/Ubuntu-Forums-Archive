---
title: "Upgrade to 11.4 Fail"
date: 2011-09-03
forum: Installation &amp; Upgrades
---

### Post by huangyingw on 2011-09-03
Hello,
     I got to stuck splash screen after upgrading to ubuntu11.4 natty.
     The confusing thing is that if I choose recovery mode at grub stage, and then failsafe mode, then I could successfully boot into graphical mode, without the unity support. And the graphical effect is the same with the normal boot mode.
     My display card is ATI Radeon HD 5600/5700, and my monitor is SAMSUNG P2450, 24 inch.
     It's a little inconvenience under failsafe mode....
     Could someone help me to debug and solve this issue?

---

### Post by huangyingw on 2011-09-04
Finally, it works after the following steps:
1. In the software-center. search "ati driver"
2. Install "ati binary x.org driver"
3. reboot.

---

