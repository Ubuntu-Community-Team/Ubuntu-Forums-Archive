---
title: "Upgraded ubuntu causing problem even after reinstallation"
date: 2011-02-10
forum: Installation &amp; Upgrades
---

### Post by rathodsachin20 on 2011-02-10
I had installed Ubuntu 10.04 inside windows 7, using wubi. But after upgrade, I couldn't boot into ubuntu, though in windows. So, i tried to change grub file using live cd as given in thread : [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)  (Refering to #Problem 2).
But, it didn't help. So, I uninstalled Ububtu and reinstalled it. But the problem still remains.
I cannot install it in the same drive partition (C:/) as before. I have installed Ubuntu 10.10 in another drive partition (E:/) and it is working fine there.
Can anyone tell the reason behind it? Will it cause any problems later?

---

### Post by Rubi1200 on 2011-02-10
If this is a fresh install, make sure you lock the grub packages according to the directions in the Wubi Megathread (main post just after the Permanent Fix section).

This should hopefully prevent problems for the foreseeable future.

---

