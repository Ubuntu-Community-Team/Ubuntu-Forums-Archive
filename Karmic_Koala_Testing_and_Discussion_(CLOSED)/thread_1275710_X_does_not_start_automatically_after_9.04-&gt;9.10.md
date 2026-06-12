---
title: "X does not start automatically after 9.04-&gt;9.10 upgrade"
date: 2009-09-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by filimon1978 on 2009-09-26
Hi all,
I updated i386 Kubuntu 9.04 to 9.10 and now upon boot I get only console screens. Login in and entering startx starts X+KDE normally. I guess it is only a quick fix somewhere.. (but where, there is no inittab...?). Thanks,
filimon

---

### Post by ilicuus on 2009-09-26
I'm having the same problem!

---

### Post by taavikko on 2009-09-26
[https://bugs.edge.launchpad.net/ubuntu/+source/gdm/+bug/434361](https://bugs.edge.launchpad.net/ubuntu/+source/gdm/+bug/434361)

---

### Post by slakkie on 2009-09-26
> **taavikko said:**
> [https://bugs.edge.launchpad.net/ubuntu/+source/gdm/+bug/434361](https://bugs.edge.launchpad.net/ubuntu/+source/gdm/+bug/434361)

Since he is using Kubuntu I expect him to run kdm, which has this bug report: [https://bugs.launchpad.net/bugs/437067](https://bugs.launchpad.net/bugs/437067)

The solution works for me.

---

