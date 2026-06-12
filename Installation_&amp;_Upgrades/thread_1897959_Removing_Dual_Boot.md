---
title: "Removing Dual Boot"
date: 2011-12-20
forum: Installation &amp; Upgrades
---

### Post by henderson63 on 2011-12-20
Currently Dual boot setup of Ubuntu and Windows 7, but never use Windows7.

Thinking I should use it virtually when I need it. I guess I can reformat the windows partitions and edit the grub configuration.

I also have a 50GB SSD that I want to use to boot ubuntu from. Anyone got any tips to do this without reinstalling the whole system.

All suggestions accepted.

---

### Post by raja.genupula on 2011-12-20
1...Boot into ubuntu
2...Open disk utility
3...Format windows partition
4...open your terminal , type this "sudo update-grub" with out quotes in your terminal

all the  best.

---

### Post by darkod on 2011-12-20
Are you talking about moving ubuntu to another disk (the SSD)?

---

### Post by henderson63 on 2011-12-20
> **darkod said:**
> Are you talking about moving ubuntu to another disk (the SSD)?
It's only a 50gb SSD, so I was only think certain partions. Such as /boot etc, the ones that take advantage of the SSD. Can I do this while booted into Ubuntu?

---

### Post by henderson63 on 2011-12-20
> **raja.genupula said:**
> 1...Boot into ubuntu
2...Open disk utility
3...Format windows partition
4...open your terminal , type this "sudo update-grub" with out quotes in your terminal

all the  best.
Good idea, forgot about that.

---

### Post by darkod on 2011-12-20
> **henderson63 said:**
> It's only a 50gb SSD, so I was only think certain partions. Such as /boot etc, the ones that take advantage of the SSD. Can I do this while booted into Ubuntu?

A 50GB is more than plenty for ubuntu. Of course, not for all of the data, depending what you have there. Just for comparison, a freshly installed ubuntu desktop is about 4GB.

You can definitely move all the / partition there, not only /boot. And you don't actually need separate /boot partition, unless you have some specific setup.

You can always use other disks for the data, / should fits just nicely in 50GB.

If you decide to go this way, you can google for "moving root to another disk in ubuntu" or similar, there should be plenty of resources online.

---

### Post by henderson63 on 2011-12-21
Thankyou, I now have an idea of how to do it. A few days off at christmas seems like a good time do it.

---

