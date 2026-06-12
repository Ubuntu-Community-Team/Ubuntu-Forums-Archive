---
title: "Open multiple LUKS partitions at boot"
date: 2014-04-30
forum: Installation &amp; Upgrades
---

### Post by elventear on 2014-04-30
I have a setup where I have 4 LUKS partitions that need to be mounted at boot time in order to assemble a RAID10 btrfs partition holding the root partition of my system.

I was able to finalize the setup fine, but when I try to boot into the system it just doesn't work. I started mucking around I have noticed that it seems that the crypto hook for initramfs only will setup one partition from `crypttab` boot time, this information is inserted into the `cryptoroot` configuration within the initramfs image.

I was able to make the system boot by adding a hacky script into initramfs that will execute before everything else that will open the other LUKS partitions.

Is there a way to achieve what I want with the standard infrastructure? I will I have to start maintaining my own initramfs script in order to achieve what I want?

---

