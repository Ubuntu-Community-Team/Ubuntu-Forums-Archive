---
title: "Share HDD with existing OS"
date: 2010-12-06
forum: Installation &amp; Upgrades
---

### Post by Poloski on 2010-12-06
Hi I've downloaded the ubunto latest install and everything went well but I didn't make enough space to share with my windows xp  OS... Ubunto has become an OS option    pre boot mode but needs more room to execute fully .everything on XP op is still fine I just need advice on what is the best way to proceed from here ...cheers

---

### Post by pricetech on 2010-12-06
If you've just installed, reinstall is your easiest option.

Make sure that you defrag windows before you shrink the partition and let windows scandisk after you resize.

Welcome to the community.

---

### Post by Poloski on 2010-12-06
ok thanks for the welcome.... I will give reinstall a try cheers Poloski

---

### Post by Poloski on 2010-12-06
ok thanks for the welcome.... I will give reinstall a try cheers Poloski

Any other links to do what you suggest would be appreciated ...How do I uninstall what is there already so I can set  up  HD with more space?

---

### Post by Poloski on 2010-12-07
Hey thanks Pricetech I looked into it and now understand what you have suggested..I may resize hd partition (it's a new computer  with heaps of space but not on the c drive) ...as far as I can tell Its possible to use GParted...freeware to help shrink then resize the c partition...giving more room for 2 OS...do you or anyone else know about this stuff ...cheers 4 now

---

### Post by pricetech on 2010-12-07
The Live CD has gparted on it.  You'll find it listed as Partition Editor as best I recall.

Defrag first, then boot to the Live CD and downsize your Windows partition.  Reboot into windows and let it run chkdisk like it wants to.  Once should be enough, but rebooting to be sure it's happy won't hurt.

Then install Ubuntu on the free space created.

Your "old" Ubuntu partition can be removed with gparted as well.  Just be careful that you remove / resize the right partitions and make a backup of your data under Windows just in case.

---

