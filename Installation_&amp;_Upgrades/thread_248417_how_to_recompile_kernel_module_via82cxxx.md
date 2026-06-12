---
title: "how to recompile kernel module via82cxxx"
date: 2006-09-01
forum: Installation &amp; Upgrades
---

### Post by shinta42 on 2006-09-01
Hi all, I just finished installing Ubuntu on my harddrive a few days ago. During this time I realized that the kernel module via82cxxx does not support the Via VT8237A southport bridge which is used by my motherboard. Due to this problem I was stuck with the problem of "cannot enable DMA for my hardrive". 

Now after a couple days of searching the internet I found out I had to edit via82cxxx.c and a header file in order for the kernel to detect the southport bridge.

Now my question is, is there a way to just recompile the via82cxxx module after adding these few lines in the source code without compiling the whole kernel?

thanks

---

