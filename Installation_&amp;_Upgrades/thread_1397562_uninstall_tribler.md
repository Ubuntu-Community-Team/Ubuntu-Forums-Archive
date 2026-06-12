---
title: "uninstall tribler"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by djdan2k8 on 2010-02-03
Hi just wondering if anyone can help me with uninstalling Tribler.

iv  tried add/remove programs and synaptic but can figure it out.


Thanks in advance

---

### Post by Ilvolanterosso on 2012-02-14
just type 

sudo dpkg -r tribler

in the terminal window

---

### Post by raghaven.kumar on 2012-02-14
You can also check if your having the right package name using
```
dpkg -l "*tribler*"
```

---

