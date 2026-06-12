---
title: "kernel upgrade to 2.6.32-23-generic-pae breaks fglrx"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by smoosh on 2010-06-30
So, first, let me explain my set-up. I have an ATI radeon HD 3400 series video card, and the open-source drivers make my computer run really hot. I tried installing FGLRX by using "Check For New Hardware Drivers", but it did not work, so I installed the ATI catalyst 10.5 package from AMD's website, and am using Xserver-xorg-core-1.7.6-2ubuntu7+backclear1 from k0ekk0ek's PPA so there is no lag when minimizing windows and such.

Everything was perfect until the 2.6.32-23 kernel update came along. I let it update, and rebooted, but the ATI driver no longer starts, even when I uninstall and reinstall it. 

Anybody know how to fix this? I am just using the 2.6.32-22 kernel for now, as the 2.6.32-23 kernel still runs hot without the ATI driver enabled. I would like to start using the new kernel at some point...

Thanks!

Smoosh

---

### Post by smoosh on 2010-06-30
Just tried the catalyst 10.6, which does not work.

---

### Post by smoosh on 2010-07-01
Works every time. I start a thread, noodle a bit, and it miraculously works when 5 minutes earlier by doing the exact same thing it didn't. huh.

---

### Post by Tumex on 2010-07-01
Hey there! I am having the same issue, could you please tell me what you did?

---

### Post by Gorlist on 2010-07-01
ditto

---

