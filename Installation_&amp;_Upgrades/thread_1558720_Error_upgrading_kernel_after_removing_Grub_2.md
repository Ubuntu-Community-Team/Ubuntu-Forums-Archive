---
title: "Error upgrading kernel after removing Grub 2"
date: 2010-08-22
forum: Installation &amp; Upgrades
---

### Post by dsmithhfx on 2010-08-22
Hi,

During a recent kernel upgrade of Karmic 64-bit (through auto-update), I noticed that Grub 2 was taking a ridiculous amount of time to find and identify every old kernel, as well as every other bootable partition on my very-multi-boot pc (there are at least 10 other distros including several Windows versions on board).

I don't actually use Grub 2, but boot Karmic directly from another distro (opensuse as it happens), using grub "legacy", which I much prefer over Grub 2. 

So I decided to remove Grub 2 from Ubunutu using Synaptic. This proceeded uneventfully and I had no problem rebooting using grub legacy as before removing Grub 2.

Now however a new kernel upgrade/patch comes along, and certain upgrade scripts can't find Grub 2, so the upgrade fails.

Any suggestions on how to get upgrades without Grub 2?

Thanks

---

### Post by HeadHunter00 on 2010-08-22
How about compiling kernel? Although, I don't think you should bother much about the kernel upgrade since it's a minor one anyways.

---

