---
title: "New Kernal upgrades add entries to Grup Boot"
date: 2011-03-25
forum: Installation &amp; Upgrades
---

### Post by Coastalguy on 2011-03-25
It seems that everytime I do a Ubuntu update, which includes a Kernal upgrade, that 2 new entries are added to my Boot screen. I now have 4 each of the main bootup lines along with a recovery line. Can anyone advise how I can edit this remove the old ones?

---

### Post by drs305 on 2011-03-25
Grub 2 will add the kernel and recovery option for each new kernel.

To limit the number displayed, you can 1) hide them (see the [_Customizer_]("http://ubuntuforums.org/showthread.php?p=10340183#post10340183") link in my signature line) or 2) remove the older kernels (see [_Remove Kernels_]("http://ubuntuforums.org/showthread.php?t=1587462")).

It's normally recommended to keep at least one older kernel you know works.

And for removing kernels, I really like Ubuntu Tweak as a GUI tool for doing this. It's included in the second link I provided.

---

