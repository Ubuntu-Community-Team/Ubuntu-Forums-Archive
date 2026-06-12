---
title: "Cannot install eclipse-base - needs gij-4.0"
date: 2006-10-06
forum: Installation &amp; Upgrades
---

### Post by ishields on 2006-10-06
I am trying to install eclipse on an AMD64 system running Dapper Drake ( 2.6.15-27-amd64-k8). Attempting to install eclipse-base through synaptic or apt-get results in failure:
eclipse-base: Depends: gij-4.0 but it is not installable
dpkg -l shows
gij            4.1.0-1        The GNU Java bytecode interpreter

Looks like the eclipse packagtes depend on a back-level gij. Any suggestiosn or pointers?

Ian.

---

