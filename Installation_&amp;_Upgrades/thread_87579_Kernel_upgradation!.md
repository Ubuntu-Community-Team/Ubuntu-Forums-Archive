---
title: "Kernel upgradation!"
date: 2005-11-08
forum: Installation &amp; Upgrades
---

### Post by Arinux on 2005-11-08
Hey all,
This is my first post and i am a beginer in this field.
I got a hp compax nx6120 notebook.
I installed ubuntu with the 386 kernel that is 2.6.12
Then going thru kernel.org upgraded it to 2.6.14 with vanilla patch using a step by step article.
But my processor is intel centrino.And lot of people told me that i have to use 686 kernel.
If yes then can some provide me a step by step guide on how to upgrade to the latest 686 kernel and remove rest all kernels which i have( my grub shows both 2.6.12 and 2.6.14 path which are based on 386)
Hopefully during this process nothing should be lost from my system right?
Ya and what kernel configuration should i give so that my laptop has following features:-
Acpi enabled ( Hibernating etc)
Optimized for gaming
Hoping for a positive reply.

---

### Post by Kyral on 2005-11-08
If you compile a kernel on your machine, it is optimized (at least in the sense of compiling) for your machine, like for any particularities your processor may have (every processor is slightly different), so it will run better than the EXACT SAME configuration that was precompiled someplace else. This is actually the philosopy behind Gentoo Linux.

As for options, believe it or not, the help system in menuconfig is VERY helpful and verbose. Give it a try :D

---

