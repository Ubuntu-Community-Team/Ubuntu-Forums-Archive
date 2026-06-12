---
title: "Installing Libglut without X?"
date: 2013-03-02
forum: Installation &amp; Upgrades
---

### Post by mattlach on 2013-03-02
Hey all,

I'm trying to set up a headless CUDA number crunching system.

The CUDA 5.0 installer depends on libglut, which means I have to install freeglut3, freeglut3-dev and binutils-gold.

Problem is, when I try to install these using apt, X is set up as a dependency, which I KNOW it shouldn't have to be.

Anyway, is there a good way to install libglut without hvaing apt pull in all of X and its dependencies?

This is on Server Edition 12.04

Thanks,
Matt

Edit:  It appears to be only Freeglut3-dev that is trying to pull in all of X.   Maybe I can do without the dev package...

---

