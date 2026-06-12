---
title: "Slow kernel boot when not using Installer."
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by BucksBell on 2011-02-03
Hello All,

I'm trying to achieve something very similar to the post below related to cloning a Ubuntu system.

I've taken a base install 10.04 from the alternatives cd.

Tweaked a few things, installed a hand rolled minimal kernel - for a quick boot.

The kernel boot on the original system is now around 2 seconds. Great!

I created a clone image of this system, by dd'ing a new file with if=/dev/zero to the correct size. Then creating an fs inside this file by doing a mkfs -t ext4. I then loopback mount the new empty file system and cp -a the source O/S directory by directory.

Again great. Now I dd the image to a new disk, install grub and boom it all works!

Except the kernel boot on the target system (clone) has slowed from my blistering 2 seconds to 12 seconds.

Hmm.

So I remove /var/lib/ureadahead/pack thinking maybe it needs to reconfigure.

Still slow.

Does anyone know why a Ubuntu system installed by the stock installer would give nice quick kernel boot, but by cloning that system using the above dd and cp -a would be sooo slow to start the kernel ?

TIA

---

