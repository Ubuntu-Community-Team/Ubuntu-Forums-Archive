---
title: "How to resize partitions?"
date: 2011-06-13
forum: Installation &amp; Upgrades
---

### Post by higashi on 2011-06-13
I'm dual booting Ubuntu with Windows7. Instructions I've found on how to resize partitions tell me to open gparted and shrink things from there. However, I can't seem to do this because:

-I can't expand the windows partition because i first need to shrink the linux partition
-I can't shrink the linux partition because it is mounted
-I can't unmount the linux partition because it is being used.

So how exactly do I expand my Windows partition?

---

### Post by Quackers on 2011-06-13
You can't change partitions which are mounted. You can use gparted from its live cd or, alternatively, from an Ubuntu live cd/usb desktop. The partitions are then not mounted.

---

