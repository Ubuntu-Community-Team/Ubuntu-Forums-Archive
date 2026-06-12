---
title: "How would I uninstall old kernels after recent dist-upgrade?"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by madmax.santana on 2010-01-04
I upgraded Ubuntu and noticed that it had installed the new kernel. That's good, but when I start my PC, old kernels also appear in my OS choice menu which appears very unorganized and shabby.
1 way is to manually edit my grub.conf file and comment out older kernel entries. But they are consuming space anyway, so why not completely remove them?
Is there a proper way?

---

### Post by MelDJ on 2010-01-04
remove it in synaptic

---

### Post by madmax.santana on 2010-01-05
a-an!!! I know that pal... I need directions, the proper way... What would i type after "apt-get remove"...

---

### Post by darco on 2010-01-05
In synaptic, search for linux-headers. Choose the old kernel. Mark for complete removal, it will also tag the generic hearders as well. Then search for linux-image, mark it for complete removal. Click apply.
If you have grub2, run update-grub in a terminal and it will remove it from the menu list on boot up. If you have grub legacy, I believe you need to edit the grub menu.lst


darco

---

### Post by madmax.santana on 2010-01-05
Okey dokey!!! Thanks guv!

---

