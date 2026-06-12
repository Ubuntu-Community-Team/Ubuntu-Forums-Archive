---
title: "Debootstrap Errors on Two Different Install Images"
date: 2012-07-01
forum: Installation &amp; Upgrades
---

### Post by buzzingrobot on 2012-07-01
I'm getting an identical "debootstrap" error at the same point in the install with both the mini.iso and the alternate ISO image (12.04), followed by a cascade of other errors if I tell it to try again.

What's going on?

(Tried a "regular" image.  As usual here, it doesn't work.  Boots into the purple screen, then a black screen, then the machine locks up. That's due to the kernel bug re: nouveau and my Nvidia card.  Again, as usual, can't get to a grub prompt.  Can only get to the "boot:" prompt.  None of the offered options will boot.)

---

### Post by buzzingrobot on 2012-07-01
My mistake. (Imagine that).

I was sizing partitions in megabytes, not gigabytes.  Only off by a factor of 1000.

---

