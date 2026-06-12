---
title: "&quot;Repair&quot; with Raid md mounts"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by Kleenux on 2010-05-19
I must say, my Ubuntu 10.04 is pretty messed up:

after trying whatever possible to get a sound card working (recompile alsa, adding modules, change configs at many places, playing with /proc/* etc...), and ***then*** remove that sound card, the system is pretty unstable:

- when the sound plays (from motherboard), it happens frequently that the application (Firefox, Totem etc...) just does a seg fault and disappears from the radars.
- much scarier: I did some downloads with FF (after playing some sounds) and the CRC of the .gz / .tar was wrong! Opera also crashes now at times.


**=>** my idea was to reinstall *only* the system then applying the updates again.

But most of the mounts are Raid 1 (MD), and the install menu (partitions) does not read the previous /etc/fstab. I guess it won't re-partition, but it may affect one of the 2 FS (combined to make 1 MD), then the raid is lost for that partition.

**Any suggestions** on the best way to recover the system with MD partitions? 
Thanks.

---

### Post by Kleenux on 2012-05-13
Oh I had to give an update on that (since you were all waiting)

The problem was actually a RAM problem. 

Bought some cheap 4 Gigs (to get to 8G) and memtest86 confirmed that 25% of the RAM was faulty, ie one of the two new/cheap memory modules.
This was not an easy one, especially since the module was representing the high memory range :-(

---

