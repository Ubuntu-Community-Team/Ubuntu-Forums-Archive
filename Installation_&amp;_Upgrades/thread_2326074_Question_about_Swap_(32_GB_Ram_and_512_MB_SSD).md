---
title: "Question about Swap (32 GB Ram and 512 MB SSD)"
date: 2016-05-28
forum: Installation &amp; Upgrades
---

### Post by isidoro4 on 2016-05-28
With 32 GB Ram and 512 MB SSD...The Question is Do I need 6 GB of Swap partition for no hybernation and 38 GB for hybernation? I Saw the scheme in the help section of Ubuntu Site.

Hybernation yes or not? Swap partition or swap file. In internet I found different and not homogeneous information.

---

### Post by sudodus on 2016-05-28
I don't know how you are using your computer, but if I had 32 GB RAM, I would need no swap space at all.

If you want to be warned, when your RAM is getting almost full, you can have for example a 2 GB swap partition, and notice that things slow down before your program crashes because of lack of memory. You need as much swap space as RAM in Gibibytes (base2), rounded upwards to whole GB (base 10), 32 GiB ~ 35 GB for hibernation.

So I think that you need less drive space for swap, than you suggest, but the difference is small, and if you want to be on the safe side, your suggested swap sizes are good :-)

Do you really need hibernation? Today computers boot linux rather quickly. I never hibernate my computer.

---

