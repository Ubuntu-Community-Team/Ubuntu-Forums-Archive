---
title: "Dapper SATA array works with Breezy kernel"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by therunnyman on 2006-06-05
Whoa, huh? On the SATA DIsk of Science and Justice, I installed Breezy, then dist-upgraded. GRUB, on reboot, showed me Dapper's kernel and Breezy's kernel; I thought, well, better have a look.

Dapper runs, and recognizes my SATA array properly.

Just more info for any developer who might come across this or any other thread regading SATA arrays and RAID construction during installation. Dapper - no matter what you install it from - writes a udev that misassigns device names and numbers, causing the "waiting for root fs" problem, and Dapper, for some reason, runs properly on Breezy's kernels (both 2.6.12-10-386 and 2.6.12-10-686.

C'mon devs...at least tell us how to do it. I'm sure we could even make our own .iso, and I'm sure someone will volunteer hosting space.

runny

---

