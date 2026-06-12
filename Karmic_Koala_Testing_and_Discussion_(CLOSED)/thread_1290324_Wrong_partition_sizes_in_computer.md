---
title: "Wrong partition sizes in computer:///"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by coffeecat on 2009-10-13
I've only just noticed this on a Karmic system fully-updated an hour ago. The attached screenshot tells all - the HD is 320 GB, not the individual partitions. In Jaunty, the icons in computer:/// will show the individual partition sizes. Looks like a bug. Is anyone else getting this?

---

### Post by xtoudi on 2009-10-13
the same here

---

### Post by VMC on 2009-10-13
I get the same thing, but I don't know if that's on purpose. It conveys that your partitions is on xxx GB Hard Drive. So if you have a different size hard drive you would know which one. If it stated the size of the partition you wouldn't know which hard drive.

So if indeed its on purpose you can state your dislike and then see if it gets changed.

---

### Post by coffeecat on 2009-10-13
**VMC**, thank you. You are right - it does seem to be on purpose. I hadn't looked at it that way.

I've just booted up a desktop with two hard drives with Karmic Beta I haven't updated yet, and it does appear as you say: either "160GB Hard Drive" or "250GB Hard Drive" with the partition labels underneath, or, with an unlabelled partition, "11GB filesystem". It would be interesting to know what would happen on a machine with two identical-sized drives.

Anyway, not a bug - I was jumping to conclusions. No wonder I couldn't find this on Launchpad. :oops:

---

### Post by Longinus00 on 2009-10-13
I think this might be confusing for many people, especially those without an understanding of how computers work.

It doesn't really matter which physical hard drive a particular partition is on, it's not like swapping hard drives is an everyday occurrence. Maybe they should just display the extra detail for removable drives?

---

