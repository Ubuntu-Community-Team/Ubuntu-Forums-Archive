---
title: "Keep the same MBR?"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by blake1 on 2008-02-07
I received a Dell Vostro 1700 laptop for Christmas with Windows Vista preinstalled on it.
It has a 10GB recovery partition and a 150GB Vista partition on the HD.

When I installed Ubuntu 6.06 last year on my main Dell machine, it erased the old Dell MBR with the recovery settings on it and put GRUB in its place. I managed to fix this with DSRFix and removed the Ubuntu partition.

But, I really want to install it now, but dont know how to dual boot while keeping my current MBR. I hear you can install GRUB on a /boot partion?

Thanks very much for your help. :)

---

### Post by confused57 on 2008-02-07
> **blake1 said:**
> I received a Dell Vostro 1700 laptop for Christmas with Windows Vista preinstalled on it.
It has a 10GB recovery partition and a 150GB Vista partition on the HD.

When I installed Ubuntu 6.06 last year on my main Dell machine, it erased the old Dell MBR with the recovery settings on it and put GRUB in its place. I managed to fix this with DSRFix and removed the Ubuntu partition.

But, I really want to install it now, but dont know how to dual boot while keeping my current MBR. I hear you can install GRUB on a /boot partion?

Thanks very much for your help. :)
You may want to look into EasyBCD:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

Make sure to install grub to the root partition when you install Ubuntu, by clicking on the "Advanced" button(last step, I believe), then type in your root partition, e.g. /dev/sdb1.

---

