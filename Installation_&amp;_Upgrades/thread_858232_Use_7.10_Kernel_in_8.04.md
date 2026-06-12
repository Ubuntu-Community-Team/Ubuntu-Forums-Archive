---
title: "Use 7.10 Kernel in 8.04"
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by liquidfunk on 2008-07-13
I feel like a complete newbie asking this question but, is it possible to upgrade Ubuntu from 7.10 to 8.04, but keep the 7.10 Kernel?

 Would that work and still allow all the updated dependencies from 8.04 to function as though it was 8.04? 

 The reason I ask is that a friends laptop works completely out of the box with 7.10 - Wireless, Sound, Graphics, Webcam, even the scrolling volume on the front. However, 8.04 doesn't work at all, the wireless doesn't work, nor the graphics. 

 Not that 7.10 is outdated, but at some point when the support stops, she won't be able to use some packages without the updated dependencies.

 Ideas?

---

### Post by liquidfunk on 2008-07-15
Bump

---

### Post by Archmage on 2008-07-16
7.10 will be supported till 18 months after the release. So you still can use it till April 2009.

---

### Post by Sef on 2008-07-16
> I feel like a complete newbie asking this question but, is it possible to upgrade Ubuntu from 7.10 to 8.04, but keep the 7.10 Kernel?

If you upgrade you will have the 7.10 kernels too.  I know you could set it as the kernel to boot into.  I'm not sure how to do that, so I will let someone else answer that part.

---

### Post by Pumalite on 2008-07-16
Edit menu.lst and change the value of 'default=0' to 'default=?' depending on the position your 7.10 kernel occupies in menu.lst; keeping in mind that Grub starts to count from 0

---

