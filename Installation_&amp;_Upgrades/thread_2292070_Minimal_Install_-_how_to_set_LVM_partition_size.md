---
title: "Minimal Install - how to set LVM partition size?"
date: 2015-08-24
forum: Installation &amp; Upgrades
---

### Post by andrew102 on 2015-08-24
OK, so normally I do a full DVD installation. Unfortunately all I had spare were some CD's (won't fit 1GB iso) so decided to do minimal Install (mini.iso) version installation.

When I get to partitioning, I choose the option to create LVM. Then all I am able to do is choose full disk size (or a percentage).

I cannot seem to choose the BOOT partition or swap size.

/boot defaults to around 250MB which I believe is too small (I've seen /boot reach 95% usage when doing kernel updates on a 500MB partition)

And the swap defaults to 6GB, however I will soon be installing an extra 2GB of RAM, so I'd like to change this to 8GB partition.

Could anybody please direct me as how to do this from minimal installation method?

---

### Post by v3.xx on 2015-08-25
Seen this?

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093)

---

### Post by andrew102 on 2015-09-09
The only problems I've had with auto-remove is when forgetting to power cycle and run apt-get update.

I ended up changing my mind and going with a different PC that already had over 8GB of RAM and a larger swap partition.

I think the solution is to select "Expert Install" > Then add the optional installation package "parted" to unlock the manual partitioning options.

---

