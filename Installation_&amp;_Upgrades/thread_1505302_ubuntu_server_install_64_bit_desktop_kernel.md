---
title: "ubuntu server install 64 bit desktop kernel"
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by loarf on 2010-06-09
So this is my first post and I am pretty new to Linux and ubuntu...here it goes!

I just installed ubuntu server 10.04 (the 64 bit version).

I would like to install the 64 bit desktop kernel and ideally be able to use either Kernel at will, and if not I would prefer the desktop Kernel for now.

Googling around a bit I found some instructions which said to:
sudo apt-get install linux-generic linux-restricted-modules

When I do this it says:

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package linux-generic

looking at /etc/apt/sources.list I have:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
which I think should cover linux-generic

Anyways, does anyone have any idea of what is going on and if I am even approaching this the right way to be able to use either kernel?  Thanks!

edit: sudo apt-get update fixed some of it but now it can't find linux-restricted-modules

---

### Post by zvacet on 2010-06-09
I think you should look for **linux-image** package.If you plan to use your comp as server tehn you don´t need desktop kernel.If you want to use Ubuntu as desktop on your machine install desktop version.

---

