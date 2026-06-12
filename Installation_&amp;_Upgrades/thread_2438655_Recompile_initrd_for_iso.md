---
title: "Recompile initrd for iso"
date: 2020-03-15
forum: Installation &amp; Upgrades
---

### Post by ping-wu on 2020-03-15
With the most recent daily builds, I am no longer able to boot from my customized LiveUSB (with boot/EFI, casper, casper-rw, and home-rw in separate partitions).  I suspect the reason being the new initrd no longer mounts the ext4 partitions during boot.  This problem has been reproduced many times, with both 20.04 and 19.10.  No problem with daily builds downloaded a few weeks ago.

How do I recompile the initrd in the most recent daily builds so it behaves just like in the original 19.10 iso (or in both 20.04 and 19.10 daily builds just a few weeks ago)?

---

### Post by ping-wu on 2020-03-16
It appears that this problem can be solved by changing the "casper-rw" label to "writable".

---

### Post by sudodus on 2020-03-16
Yes, you are right: The version of Focal Fossa, that you get via the current daily iso files want the name/label 'writable'. This affects standard Ubuntu and all community flavours, because they use the same version of the casper package.

You find more details at [this bug report](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1863672).

---

