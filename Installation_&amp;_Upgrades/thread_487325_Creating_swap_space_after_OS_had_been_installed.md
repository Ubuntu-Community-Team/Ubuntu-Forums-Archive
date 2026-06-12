---
title: "Creating swap space after OS had been installed?"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by theb on 2007-06-28
Hi,
I installed feisty and didn't create a swap space initially.  How would I go about adding it in now considering I already installed everything?

Thanks

---

### Post by coldstatue on 2007-06-29
Go into Administration and open Gnome Partition Manager. Make sure you select the drive you want swap on. Is there any space (preferrably at the end of the drive) to create a partition? 2 Gigs is pretty standard, depending on how much RAM you have. If not, will you have to resize the same partition that your Ubuntu install is on? If you need to resize your Ubuntu partition, you will need to boot off of a livecd, or into another linux distro, if you have one. You cannot resize a partition while it is mounted (being used by your system.)

Take a look in GPartEd, and post what you see and know about the partition(s) in there.

---

