---
title: "Multiple directory paths per partition"
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by finni on 2010-11-05
Is there a way to give multiple mount points to one partition? What I mean is for.ex. giving /boot and /var to partition /dev/sda1 ?

Can this be done without symbolic links and preferably at ubuntu installation sequence?

---

### Post by finni on 2010-11-05
> **finni said:**
> Is there a way to give multiple mount points to one partition? What I mean is for.ex. giving /boot and /var to partition /dev/sda1 ?

Can this be done without symbolic links and preferably at ubuntu installation sequence?

Mount with bind/rbind seem to be what I'm looking for. This is not possible when installing though.

---

