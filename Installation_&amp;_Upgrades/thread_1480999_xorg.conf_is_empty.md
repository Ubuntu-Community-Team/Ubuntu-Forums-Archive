---
title: "xorg.conf is empty"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by Moustaffa on 2010-05-12
Hi all,

I was looking at tutorials to try to install the ATI Radeon Xpress 1150 (RS480) manually, but they say something about editing xorg.conf.

The problem is that this file is empty, so I can't adjust sections. 

What to do?

By the way, has anyone ever successfully installed the driver for my graphics card?

Thanks in advance

---

### Post by dino99 on 2010-05-12
lucid dont need xorg.conf by default, what you need to install from synaptic is: xserver-xorg-video-radeon (then check: system admin hardware driver to see if its activated)

but if you want to built a xorg.conf, you have to run :

sudo aticonfig --initial -f

---

### Post by realzippy on 2010-05-12
The ATI fglrx driver does not work for your card...unless you run Ubuntu 8.10 or older.
The free ATI driver should work out of the box without editing xorg.conf,
so everything should be ok.

---

### Post by realzippy on 2010-05-12
> **dino99 said:**
> lucid dont need xorg.conf by default, what you need to install from synaptic is: xserver-xorg-video-radeon (then check: system admin hardware driver to see if its activated)

but if you want to built a xorg.conf, you have to run :

sudo aticonfig --initial -f



???? isn't that **only** for fglrx??

---

### Post by wilee-nilee on 2010-05-12
Try this ppa it enabled a radeon card in a older dell inspiron.
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

