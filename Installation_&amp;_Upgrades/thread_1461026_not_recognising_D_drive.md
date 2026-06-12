---
title: "not recognising D drive"
date: 2010-04-23
forum: Installation &amp; Upgrades
---

### Post by gajrajiitr on 2010-04-23
I have installed ubuntu in my D drive on my lenovo laptop but it not recognizing D drive only recognize C drive

---

### Post by efflandt on 2010-04-23
D drive is a Windows term and does not tell us if it is a primary or logical partition or if it is on a totally different drive than your C drive.  If Windows uses disk volumes instead of partitions, that could throw a wrench in the works.

I don't know if there is anything peculiar about installing to Lenovo computers, but as a start, you might post the output of **lspci fdisk -l** (small L). from an Ubuntu install CD if that works, and point out which partition you are calling D.  After you paste the fdisk output, highlight that and hit the # icon above to wrap it with code tags so it keeps its spacing.

---

