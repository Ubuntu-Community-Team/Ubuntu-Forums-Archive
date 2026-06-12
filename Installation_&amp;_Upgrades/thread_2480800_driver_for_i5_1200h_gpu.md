---
title: "driver for i5 1200h gpu"
date: 2022-11-10
forum: Installation &amp; Upgrades
---

### Post by eoushblank100 on 2022-11-10
I am new to linux.
i bought a laptop with i5 1200h cpu but while using blender it doesnot show the gpu rendering support . Do i not have a gpu driver or what is the problem ?? can anyone help me on this. and i am new to linux is ubuntu distro helpful to me??

---

### Post by ActionParsnip on 2022-11-10
What is the output of:
```

sudo lsb_release -a; uname -a; sudo lshw -C display

```

---

