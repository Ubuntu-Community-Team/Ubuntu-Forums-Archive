---
title: "adding ubuntu to grub"
date: 2008-09-02
forum: Installation &amp; Upgrades
---

### Post by prasenjit on 2008-09-02
Hi!

I already have grub setup for multi-boot with two debian systems, a winxp and a fedora system. How would I go about adding ubuntu to this grub? I will also need to install ubuntu. How would I go about this? Any help/links will be appreciated.

P.S: I didn't setup the original grub system, so I am pretty clueless.

---

### Post by Shazaam on 2008-09-02
Generally, any version (distribution) of linux that you install will automatically install it's own version of grub. When you install Ubuntu it does a good job of finding your other operating systems. I multi-boot with 3 hard drives and Ubuntu 8.04 found all 6 of the operating systems that I had already installed.
If you don't want to have that happen make sure you install grub to the new Ubuntu partition and NOT to the mbr. Then go to the distro that has control of grub and do a grub -update or you can manually add it to that distro's menu.lst.

---

