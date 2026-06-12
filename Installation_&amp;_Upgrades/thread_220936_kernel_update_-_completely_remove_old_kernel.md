---
title: "kernel update - completely remove old kernel"
date: 2006-07-22
forum: Installation &amp; Upgrades
---

### Post by odysseus.lost on 2006-07-22
Hi,

I am sure that this will be somewhere but my search is crowded with no relevant result. Basically, after updating to new kernel version using the update manager, how can I completely remove the old one?

Cheers.

---

### Post by Ares Drake on 2006-07-22
quite easy: with Synaptic (System->Administration->Synaptic) you can uninstall linux-image-"version" and linux-headers-"version", with "version" being i.e. 2.6.15-23-686

Be advised however it might be handy at some times to have an older kernel installed as a fallback, so choose wisely.

You can change the appearance of the grub bootloader (where you select your operating system to start) to display fewer kernels by editing /boot/grub/menu.lst However be sure to make a backup of that file before!!

---

### Post by 5-HT on 2006-07-22
Just to add to Ares Drake's post: you may also want to remove the restricted modules package for the kernel you're removing if it's installed (it'll have the same version number as the kernel) as you won't be needing it without the kernel.

HTH

---

### Post by odysseus.lost on 2006-07-23
OK, there is no automated/record of the kernel updates.... Actually I intent to keep my last working kernel with the latest one.... but the older ones are kind of redundant... Thanks guys...

---

