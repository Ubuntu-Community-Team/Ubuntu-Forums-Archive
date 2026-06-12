---
title: "Install on separate partion of same drive?"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by Bumpalot on 2012-04-29
Have Ubuntu 10.04 installed in 80G partition of a 480g drive. Can I install Kubuntu 12.04 in another separate partition on the same drive?

---

### Post by oldfred on 2012-04-30
Did you mean to click solved?

Yes you can have as many installs as your system can hold. But only one MBR install controls booting. So you have to decide which install is in charge - generally the one you want to boot the most. this will add the other.

sudo update-grub

I have several on one drive with data in separate partitions. Then my / (root) is only needs to be 25GB with about 7GB used.

---

