---
title: "GCC install requires CDROM?"
date: 2005-04-23
forum: Installation &amp; Upgrades
---

### Post by Paha Pukki on 2005-04-23
Hi,

I try to install GCC 3.3 using Synaptic but get the following error message:

> Please insert the disk labeled:
Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)
in drive /cdrom/


When I press Cancel, I get the following:

> W: Failed to fetch cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/pool/main/g/gcc-3.3/gcc-3.3_3.3.5-8ubuntu2_i386.deb

What am I doing wrong?

---

### Post by Burgundavia on 2005-04-23
Remove the cdrom from your sources lists. It is part of what is shipped but not installed by default.

Corey

---

### Post by Paha Pukki on 2005-04-23
Thank you Corey

---

### Post by sharp11 on 2005-05-12
Okay, dumb question: where is the "sources list"?

---

### Post by sharp11 on 2005-05-12
Okay, found it: /etc/apt/sources.list

---

