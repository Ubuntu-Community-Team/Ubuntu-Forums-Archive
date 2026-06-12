---
title: "How do I allocate a swap partition after installing ubuntu?"
date: 2012-01-18
forum: Installation &amp; Upgrades
---

### Post by damonkashu on 2012-01-18
I foolishly made the mistake of not making a swap partition on my initial installation of ubuntu 11.10 64-bit. Now I'm wondering after it's all done, is it possible to partition the drive and allocate a swap partition now? I don't have much actual data on my SSD so there is a lot of space available.

---

### Post by zvacet on 2012-01-19
You can do that with Ubuntu live CD and Gparted program.Shrink existing partition and on that unallocated space make swap partition.

---

### Post by nothingspecial on 2012-01-19
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by raja.genupula on 2012-01-19
> **zvacet said:**
> You can do that with Ubuntu live CD and Gparted program.Shrink existing partition and on that unallocated space make swap partition.

+1 after doing that at options of swap partition click at swap on .

---

### Post by damonkashu on 2012-01-19
Strange, I don't see linux-swap as an option when using gparted..

---

### Post by raja.genupula on 2012-01-20
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)
Hi look at FAQ 9 , but i actually when i have created my swap , its off and turn on by using Swap ON . 

Cheers

---

### Post by zvacet on 2012-01-20
> Strange, I don't see linux-swap as an option when using gparted..

I you shrinked exisating partition you have some unallocated space ( it is gray).Right click on it and format it as swap ( or linux-swap).

---

