---
title: "Size Matters"
date: 2005-11-22
forum: Installation &amp; Upgrades
---

### Post by Dragineez on 2005-11-22
After searching about, I think I may have come across a unique situation. At least, I can find no thread that discusses it.

I have a bright, shiny, new hard disk and I want to install ubuntu onto it. No problem right? Well, I don't want it to use the whole thing but I DO want to use LVM. I haven't managed to figure out how to tell it to use only 20GB (or 40GB, or 7.74GB or whatever). Any hints? Suggestions? Recipes?

---

### Post by aysiu on 2005-11-22
What's LVM?

---

### Post by kennethb on 2005-11-22
Is LVM "Linux Virtural Machine" what you want?

---

### Post by Dragineez on 2005-11-22
I suppose LVM stands for "Logical Volume Manager". I want the ability to expand volumes in the future which I won't be able to do (easily) if I manually partition. Even I know I could setup my own partitions, but I don't know how to tell LVM to not use the whole disk.

---

### Post by aysiu on 2005-11-22
Maybe this might help you?
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Dragineez on 2005-11-22
Well, that - like the 7 or 8 thousand others I've found - all talk about how to install when it's the second or succeeding OS you're installing. What I want is to do an initial install to an empty hard disk, using LVM, not have to spend time figuring blocks, sectors, heads, etc; and have it not use the whole disk. Oh, and world peace - I want that too. And some chocolate covered strawberries, that'd be nice. And....

---

### Post by aysiu on 2005-11-22
I didn't mean that you follow it step by step.
The idea is to figure out how to resize a partition during the installation.

If you want, you can also resize the partition before installation, using a live CD like Knoppix and a program called QTParted.

---

### Post by yesplease on 2005-11-23
Just start the install, when you arrive at partitioning, choose manual partitioning. Select the disk, make  ext3 and swap partitions of the size you want and continu install.  You can leave the rest unpartitioned and partition it later.

(Sorry to interfere Aysiu, I know your link gives the right answer too)

---

