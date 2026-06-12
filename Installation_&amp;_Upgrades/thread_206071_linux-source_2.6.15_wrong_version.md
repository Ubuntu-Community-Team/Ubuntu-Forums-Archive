---
title: "linux-source 2.6.15 wrong version ?"
date: 2006-06-29
forum: Installation &amp; Upgrades
---

### Post by phico on 2006-06-29
Hello,

I'd like to recompile the kernel.  I install latest package 
> sudo apt-get install linux-source-2.6.15

But when I unzip sources it build me 2.6.15**-7** kernel ?  
Just looked in the Makefile, it appears** EXTRAVERSION = .7-ubuntu1**

Why is it not 2.6.15**-25** like for the binary ?

---

