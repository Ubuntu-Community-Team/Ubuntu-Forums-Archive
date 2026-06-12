---
title: "Upgraded to Hardy - kernel not updated in GRUB"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by secretservgy on 2008-07-20
So I upgraded to Hardy a week ago, I have 2 ubuntu installs on this box, one's 64 bit that I don't use (nor can I log in to as I forgot the credentials), and the 32bit which I use 100% of the time. After the update and kernel upgrade, the new kernel's not listen in the GRUB boot menu. The kernel IS in menu.lst. I've tried update-grub and such - no luck. I belive the problem is because the 64bit inst. was installed after the 32, in which the GRUB boot is taken from the menu.lst of the 64bit install - I'd try to update-grub on there, but I cannot log into it. Any ideas?


EDIT: I just got a suggestion on IRC that doing grub-install on the drive would redo everything with the new kernels. Does anyone agree with this - I want an additional 'yes' before I do it.

EDIT: I did the above, fixed.

---

