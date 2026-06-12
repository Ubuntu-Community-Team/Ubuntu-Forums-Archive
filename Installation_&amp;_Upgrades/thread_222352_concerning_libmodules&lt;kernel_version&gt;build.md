---
title: "concerning /lib/modules/&lt;kernel_version&gt;/build/"
date: 2006-07-24
forum: Installation &amp; Upgrades
---

### Post by darth_vector on 2006-07-24
i dont compile my own kernels, i just get updates through aptitude. problem is, i need to compile some software (a gpib package for a uni project) that requires the stuff in this directory. how do i go about building this directory tree without having to build myself a kernel???

any help appreciated :)

---

### Post by simonn on 2006-07-25
Install linux-headers with the same version as your kernel.

Use synaptic or apt-get etc.

---

### Post by darth_vector on 2006-07-26
thanks mate :)

---

