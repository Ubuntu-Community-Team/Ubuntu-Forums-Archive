---
title: "linux boot.ini equivalent"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by dbowlin17 on 2010-03-09
I have a lot of different kernels showing up when in GRUB 2. How do I get it to stop showing me the ones I don't need? I have kernels dating back to around -15 or -16, but now I use 20... I see reason for having a few extra in case of issues, but not so many that my windows xp is almost not shown due to too many to display...

---

### Post by presence1960 on 2010-03-09
It is a good idea to keep the 2 newest kernels in case one goes south then you can boot into the other kernel.

To remove the ones you don't want go to System > Administration > Synaptic Package Manager. Mark for Complete Removal:

linux-headers-2.6.31-16
linux-headers-2.6.31-16-generic
linux-image-2.6.31-16

Click Apply at top toolbar to apply.

Just substitute the kernel #'s that you actually want to remove. This will uninstall them and remove the packages from cache.

Next open a terminal and run ```
sudo update-grub
```to refresh grub.cfg thus your GRUB menu at boot.

---

### Post by dbowlin17 on 2010-03-10
thanks. is there a way to just hide things? or do i need to remove it if i don't want it? i reduced my things to -19 and -20, i had stuff going back to -15... so thanks.

---

