---
title: "Wrong kernel-source in Synaptic"
date: 2007-05-27
forum: Installation &amp; Upgrades
---

### Post by JBull on 2007-05-27
I'm trying to install the kernel-source package for my new kernel, which is 2.6.18-4-686.  When I try to use apt-get install kernel-source it says kernel-source-2.4.27 is already the newest version.  Thats the wrong kernel-source package.  I no longer use 2.4.

I also tried apt-get install kernel-image-2.6.18 and I get 
E: Couldn't find package kernel-source-2.6.18

Using Synaptic the only kernel-source in the list is kernel-source-2.4.27.

How do i get the correct kernel-source and also how do I tell my apt-get that its looking for wrong kernel versions?

---

### Post by taurus on 2007-05-27
Can you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

