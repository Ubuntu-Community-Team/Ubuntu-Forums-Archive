---
title: "How to install an old kernel?"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by amuleto on 2008-03-25
Hi, 

I have ubuntu 7.10 with kernel 2.6.22.14-generic installed and I need to install an "old" 2.6.19/20 release. How can I do it from the Ubuntu repsositories? Is it possible?

Thanks

Amuleto

---

### Post by kpkeerthi on 2008-03-25
System -> Admin -> Synaptic -> Search

Search for linux-image-2.6.20.**xx** and mark for installation. 

* replace xx with appropriate version number

NOTE: I have not done this. I'm not sure if the kernel will be automatically added to GRUB or requires manual addition.

---

### Post by amuleto on 2008-03-25
That's the problem. it doesn't exist. Do I have to add some other repositoire from older versions to source.list?

Amuleto

---

