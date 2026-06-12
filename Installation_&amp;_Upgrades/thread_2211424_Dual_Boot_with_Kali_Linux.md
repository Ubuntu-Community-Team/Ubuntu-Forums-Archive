---
title: "Dual Boot with Kali Linux"
date: 2014-03-16
forum: Installation &amp; Upgrades
---

### Post by ArgentWarrior on 2014-03-16
Is this possible/safe? I plan to shrink my current / partition down about 10gb, but will Kali's bootloader just add an entry to the Grub menu? Or will it break Ubuntu? I'm running 14.04, if that's relevant

---

### Post by dniMretsaM on 2014-03-16
It's completely possible and safe (assuming you do it correctly). The bootloader installed by Kali (also GRUB) will recognize the Ubuntu partition and put an entry in for it just fine.

---

### Post by hpzgod on 2014-03-19
I have done this, not just with Ub13 but BSD and MS kernels ... suggestion: always run from LiveCD first ... it is a large iso 3.2GB but only requires 512MB to work. GL

---

