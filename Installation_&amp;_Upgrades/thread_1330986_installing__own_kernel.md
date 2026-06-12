---
title: "installing  own kernel"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by ciiccii on 2009-11-18
I downloaded the 6.31 and 6.32 version of ubuntu kernel form mainline, and just stripped it down, excluding modules i don't need. I can compile the kernel successfully, but after installation the /home wont be mounted(/home is encrypted). During boot process(befor login promt) i get the error message: ```
 Unable to find a suitable fs in /proc/mounts, is it mounted? Use --subdomainfs to overide
```. However i can login as roor or a regular user. But i cant mount /home with encrypted data. encrypt-private-mount fails. Also the loading of apparmor fails. On the generic kernel kernels all works great. -.- Please help.

I also tried to compile the kernel with .config from original ubuntu kernel and get the same problem.

---

### Post by ciiccii on 2009-12-03
up

---

