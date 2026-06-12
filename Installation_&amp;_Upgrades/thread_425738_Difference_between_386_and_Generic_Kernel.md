---
title: "Difference between 386 and Generic Kernel"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by allwin on 2007-04-27
I have a P-III 1.4 GHZ processor, vintage 2001, in my Linux toy box.  After I upgraded to Feisty (had Edgy previously) now my Grub menu lists the 386 kernel first and the Generic one second.  Help me here, I'm a bit of a n00b at deciphering the various classes of Intel processors.  System seems to run fine with the 386 kernel, though I believe using the Generic would be a little speedier because of newer instruction sets?

What prompted the upgrade to change its verdict on which kernel to use?

Second question, would it be wise to change to the generic instead, and how would I do that?  There's an Nvidia card with Beryl (all works OK) there now and I'm afraid if I change things to boot generic I will need to reinstall something else?

---

### Post by dhaus111 on 2007-04-28
I was running the 386 kernel with edgy, then with feisty it moved me over to the i386.  Don't know why.  anywho. I'm running a dual core proc and I noticed that resource manager was now only showing one CPU. so i switched to the generic and it was good.  However, to answer your 2nd question (no idea on q #1) , yes you'll have to reinstall your nvidia drivers and the linux-restricted-drivers.  I think there was also a meta package for the generic kernel, i'd install that also.
good luck

---

