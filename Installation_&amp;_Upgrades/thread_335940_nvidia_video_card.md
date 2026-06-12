---
title: "nvidia video card"
date: 2007-01-10
forum: Installation &amp; Upgrades
---

### Post by mistypotato on 2007-01-10
Hellooooo,

I put an nvidia MX2 400 card in my ubuntu 6.06 machine and the graphics don't really seem much improved.

Is it because I was forced to use VESA as the driver or whatever instead of "nv"?

---

### Post by rpradeep on 2007-01-11
You actually need to install the nVIDIA driver from nVIDIA website for your card.

This will give you the full potential of the card.

---

### Post by Wim Sturkenboom on 2007-01-11
Why are you forced? Does the nv driver not work?

---

### Post by mistypotato on 2007-01-11
> **rpradeep said:**
> You actually need to install the nVIDIA driver from nVIDIA website for your card.

This will give you the full potential of the card.

But I went to their site and they don't offer a Linux driver  :confused:

---

### Post by mistypotato on 2007-01-11
> **Wim Sturkenboom said:**
> Why are you forced? Does the nv driver not work?


No,

As long as I try to use the "nv" driver, I get a Xserver configuration error.
No matter what I try, I can't get it to work unless I use the "VESA" driver, but
that negates the benefit of having the nvidia card because it dosen't use it's potential.

---

### Post by bigken on 2007-01-11
you could use automatix to install the nvidia drivers ;)

---

### Post by mistypotato on 2007-01-11
Thanks Ken,

That did it :)

---

### Post by bigken on 2007-01-11
> **mistypotato said:**
> Thanks Ken,

That did it :)

cool ;)

---

### Post by penvzila on 2007-01-11
> **mistypotato said:**
> But I went to their site and they don't offer a Linux driver  :confused:

Wrong.

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by mistypotato on 2007-01-11
Well, I "should" have said "I couldn't FIND" the driver.

Automatix did the job for me.

Thanks

---

