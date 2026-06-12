---
title: "Initramfs-tools and lilo problems - solution"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by drodiger on 2007-04-22
Hi,

I did the upgrade to Feasty few weeks ago. Since the upgrade I had a problem with boot. I always ended in BusyBox, with error that root partition was not mounted. I used lilo as a boot manager, so if I wanted to boot the system I had to add root=/dev/hda1 parameter during the boot. This is, probably, due to the problem that intiramfs doesn't know where is the root. I had a root parameter in lilo.conf, but that was not a solution.

Today I added append="root=/dev/hda1" to the lilo.conf and it worked. I am able to boot without adding boot parameters :-)

Dejan

---

