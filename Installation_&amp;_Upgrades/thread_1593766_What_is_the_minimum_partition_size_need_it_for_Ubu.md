---
title: "What is the minimum partition size need it for Ubuntu netbook"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by alqin on 2010-10-11
I want to install Ubuntu Netbook Remix on my EEE PC 901.
I want to make a partition for that on the 16 gb hdd.
What is the minimum size required by the Ubuntu Netbook Remix on a fresh install?

---

### Post by mörgæs on 2010-10-12
There should be plenty of space within 16 GB. Here is an example:

Root: 4 GB
Swap: Double the amount of memory, but not more than 4 GB
Home: What you feel is necessary

---

### Post by alqin on 2010-10-12
So the minimum required space for Ubuntu Netbook is 4 GB?

I remember reading somewhere that the swap partition is not even necessary with a lot of memory. Is this  true?. I have 1 GB RAM.

---

### Post by mikechant on 2010-10-12
I have nearly the same hardware (EEE PC 1000, 1Gb RAM) and it runs quite happily without a swap partition, but it's only used for fairly light duties (e.g. Browser+video player).

There are some recommendations not to have a swap partition on an SSD (particularly a small one) since it may help wear the disk out faster, but I think it's more likely that the space would generally just go unused and be wasted.

Note you must have a 1Gb minimum swap space if you want to be able to hibernate though.

As far as root size is concerned I would say 3Gb is the bare minimum, 4Gb should be OK for most people and 5Gb would cater for installing a larger number of big software packages (not very likely on a small netbook).

---

### Post by mörgæs on 2010-10-12
There is no clear definition of how much space is necessary. A hard drive should not be filled more than 3/4, so 4 GB is a good rule of thumb.

If you are low on space, remember to clean up with 
```
sudo apt-get clean
```
once in a while.

If you plan to use suspend/resume, swap is needed. Go for 2 GB.

In general, just try something and see how it works. You can always change the partitions later using Gparted.

---

### Post by alqin on 2010-10-12
Thank you guys for helping me get start it.

---

### Post by mikechant on 2010-10-13
mörgæs said:
> If you plan to use suspend/resume, swap is needed. Go for 2 GB.

Sorry, this is wrong. You only need swap for hibernate. Suspend/resume is a low power state where your RAM contents are retained. Hibernate is a 'non-power' state where your RAM contents are written to swap and the machine then powers off.

I use suspend/resume constantly on my eeePC with *no* swap defined.

---

### Post by hecatae on 2010-10-13
depends what you need, I have previously slimmed Ubuntu down to 1.6 GB for my eeepc701 4G

---

### Post by mörgæs on 2010-10-13
> **mikechant said:**
> 
Sorry, this is wrong. You only need swap for hibernate. Suspend/resume is a low power state where your RAM contents are retained. Hibernate is a 'non-power' state where your RAM contents are written to swap and the machine then powers off.

I use suspend/resume constantly on my eeePC with *no* swap defined.

Thanks for correcting.

---

