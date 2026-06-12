---
title: "4 GB limit and swap partition"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by Shiryu on 2010-12-10
Hello,
On a 32-bits system, if ram size plus swap partition size equals 4 GB, would a bigger swap partition be useless?
Should ram size plus swap partition size be 4 GB?

---

### Post by tommcd on 2010-12-10
How much memory do you have? If you have at least 1-2GB memory then you will probable never touch the swap partition.
I currently have 3GB memory and a 1GB swap on my desktop and I am using 32bit Ubuntu. I never even touch my swap partition. My laptop has 1.5GB memory and I never touch swap on the laptop either.
Note: If you want to be able to suspend to memory, the general rule is to have a swap that is at least equal to the amount of memory that you have.
Note2: The 4GB memory limit for 32bit Ubuntu does not include swap. It pertains just to the amount of physical memory you have.

And welcome to the Ubuntu forums!

---

