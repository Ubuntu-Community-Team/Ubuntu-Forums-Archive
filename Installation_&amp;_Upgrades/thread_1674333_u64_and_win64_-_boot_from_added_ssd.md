---
title: "u64 and win64 - boot from added ssd"
date: 2011-01-23
forum: Installation &amp; Upgrades
---

### Post by jloveless on 2011-01-23
I have been using Ubuntu since 8.04. I am about to receive a new PC made with the new Intel i7-2600 processor. I want to use it for video editing in Ubuntu but would like to keep the Win install also. The PC has a 1TB drive with Win7 installed. I want to add an  32GB SDD drive as my boot drive with Ubuntu 10.10-64. I want to add a 3rd drive - 1 TB for data store of large video files.
Questions:
1. do U64 and W64 play well together?
2. Can U64 boot from the SSD drive?
3. Should I install Grub on the ssd?

I am very open to suggestions, tips, hints, etc, that will make this work the best.

Many thanks.

---

### Post by mikewhatever on 2011-01-24
1. Not sure what you mean. If you are going to install Ubuntu on a separate partition, the two OSs won't play together at all, as there is no need for that.
2. Yes.
3. Yes. You'll have to change the default grub location and make sure it's installed to the MBR of the ssd.

---

### Post by jloveless on 2011-01-24
Thanks. by "play well together" i just meant can I install U64 after w7 as easy as it has been in the past (w/U32 and Vista/XP). Sorry for the obtuse-ness. I guess if U64 and grub have to now be on the boot drive there are some differences. Why is that (just curious)?

---

### Post by mikewhatever on 2011-01-24
By using a separate ssd, you are making the Ubuntu installation completely independent of W7. There is no partitions resizing or boot loader sharing, and it doesn't matter if Ubuntu gets installed before or after.
Grub should go to the ssd cause you are going to boot from it. That hasn't changed.

---

