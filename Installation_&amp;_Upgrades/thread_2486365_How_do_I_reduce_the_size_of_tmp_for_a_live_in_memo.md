---
title: "How do I reduce the size of /tmp for a live in memory boot?"
date: 2023-04-27
forum: Installation &amp; Upgrades
---

### Post by linecks on 2023-04-27
When I boot from USB with 'toram' as a boot menu parameter and run ubuntu fully in RAM, half of the machine's RAM is assigned to /tmp, with the other half assigned to /cow (or /) 


As far as I can tell, the amount of memory allocated to /tmp can't be reduced as a boot option, and must be configured in the ISO. 


I extracted the ubuntu lunar lobster ISO and decompressed initrd with cpio but that just gave me another binary file.


Where is the ratio of ram assigned to /tmp configured in the ISO and how can i modify it? Once i know that I think i should be able to successfully rebuild the ISO from there.

---

### Post by sudodus on 2023-04-27
You can easily increase the size of /cow by creating a persistent live system with a partition for persistence. That makes the size of /cow the same as that of the file system in the partition for persistence.

Such a system will be able to store installed application program packages as well as personal data files (documents, pictures ...).

If you have an SSD connected internally or via USB3 it can be fast and big.

You can create a persistent live drive with [mkusb](https://help.ubuntu.com/community/mkusb).

---

