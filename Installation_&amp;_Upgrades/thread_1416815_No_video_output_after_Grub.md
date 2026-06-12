---
title: "No video output after Grub"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by dbbolton on 2010-02-26
After a recent update on Karmic, I have no video output after selecting a kernel from Grub- and I mean absolutely nothing but a black screen. I also removed "quiet" and "splash" from the grub entry.

The kernel (generic) does not appear to panic. It responds to the Magic SysRq keys.

I booted a live CD, chrooted into the broken system, ran "aptitude safe-upgrade", updated the initramfs for the default kernel, and ran "update-grub2". But I still don't have and video output after selecting a kernel from grub.

I am not even worried about X right now. I would just like to get at least framebuffer video working again.

---

### Post by dbbolton on 2010-02-26
Solution: installed Debian.

---

