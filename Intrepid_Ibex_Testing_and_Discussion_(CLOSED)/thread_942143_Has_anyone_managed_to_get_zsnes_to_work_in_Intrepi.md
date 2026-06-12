---
title: "Has anyone managed to get zsnes to work in Intrepid?"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2008-10-08
I am using 64-bit Intrepid, and I cannot get zsnes to run.

I installed with with: 

[code]sudo dpkg -i --force-architecture zsnes-*[/quote]

That has always worked fine for me with previous versions of Ubuntu, including Hardy. 

When I run it in Intrepid, I get:

> *** buffer overflow detected ***: zsnes terminated

If I run the version that was packaged for Hardy, I get:

> 
segmentation fault


If any of you have managed to get this working, please let me know what you did.

---

### Post by Locke_99GS on 2008-10-20
Bump.

I have the same issue with 32bit Intrepid.

---

### Post by volanin on 2008-10-20
From [this thread]("http://ubuntuforums.org/showthread.php?t=926906"):

This is caused by the hardened toolchain.
See [https://wiki.ubuntu.com/CompilerFlags]("https://wiki.ubuntu.com/CompilerFlags")

Bug Report:
[https://bugs.launchpad.net/ubuntu/+source/zsnes/+bug/250425]("https://bugs.launchpad.net/ubuntu/+source/zsnes/+bug/250425")

---

