---
title: "Seemingly extra kernel"
date: 2005-11-26
forum: Installation &amp; Upgrades
---

### Post by dsjas297 on 2005-11-26
Hello. I upgraded to Ubuntu 5.10 from 5.04 using the Synaptic package manager. However, the old linux kernel was not removed and still shows up on  the Grub boot loader. How would I remove it?

---

### Post by aysiu on 2005-11-26
Remove it remove it...? Or just remove the entry for it?

---

### Post by dsjas297 on 2005-11-26
I want the old kernel completeley removed if possible. I need all the space I can get.

---

### Post by jdong on 2005-11-26
Open up Synaptic, search up "linux-image"... Remove all the non-latest entries (in other words, leave all the 2.6.12 there.

---

### Post by dsjas297 on 2005-11-26
Worked perfectly. Thanks a lot.

---

