---
title: "lvm after partial hardware upgrade?"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by isecore on 2008-03-07
Within the not too distant future I'm going to upgrade my current machine. Currently it's a AthlonXP 2200+, 1 gig of RAM and a Nvidia FX5600. Not exactly the newest stuff around. I was thinking about getting myself a quad-core Phenom with a decent mobo, 4 gigs of RAM and a Nvidia 9600GT.

I'm not worried about Ubuntu being perfectly capable of just autodetecting whatever has changed in the machine. If for some weird reason this doesn't happen, then a reinstall is not a problem.

But I do have one question.

I have five harddrives of varying size in this machine. Four of them (three IDE and one SATA) are tied together in LVM. The fifth one (my primary SATA) is standalone, and Ubuntu lives on this drive. Now, if I upgrade to fresh hardware the positions of the drives will of course shift around a bit since newer mobos only have one IDE-channel as opposed to the two on my current mobo. That means I'll have to plug in an IDE-controller card.

So, what will this do to my LVM? I can live with losing the data on it (it's nothing vital) but I'm curious as to how flexible LVM is in this case, and whether it'll just keep on ticking or if I'll have to recreate the whole VG and everything.

---

