---
title: "Oracle kernel settings map to kernel.sem"
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by zongpog on 2010-02-02
Dear all,

  I am installed Oracle on a server (HP G6 c-class) and have a question about the kernel.sem setting in the /etc/sysctl.conf.

Oracle specifies these kernel settings:

kernel.semmsl = 256
kernel.semmns = 32000
kernel.semopm = 100
kernel.semmni = 142

However, the closest I can see it the default setting for:
kernel.sem = 250 256000 32 1024

Does this setting relate to the four settings asked by Oracle, and if so, does this list correspond to: ?
```

kernel.sem = 250    256000 32     1024
             semmsl semmns semopm semmni

```

Does anyone know?

best wishes, z.

---

