---
title: "Problem extending swap partition"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by Aramil on 2006-06-04
I decided to install Ubuntu 6.06 in an old computer that i have (which was using another Linux distro).I realised that I had to use more swap than I already had.So I formatted the whole disk but the swap partition remained.I tried to resize the swap partition but GParted popped up the msg that this partition is mounted...I tried it also with QTparted and also can't perform the operation...Any solutions?

---

### Post by aysiu on 2006-06-04
Try the ```
sudo swapoff
``` command.

---

### Post by Aramil on 2006-06-05
I tried but i get the message

/dev/hda5 Cannot allocate memory

I get the same message when i try to unmount the swap partition from the Gparted tool.Any other suggestions?

---

