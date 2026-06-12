---
title: "Copy ubuntu from external HD to computer"
date: 2012-05-16
forum: Installation &amp; Upgrades
---

### Post by PizzaLover101 on 2012-05-16
Hi.
I recently decided that I didn't want to use windows anymore due to a variety of reasons, however I have been booting ubuntu from an external HD for quite some time. Is there a way I can copy ubuntu from my external HD to my internal HD?

---

### Post by wilee-nilee on 2012-05-16
> **PizzaLover101 said:**
> Hi.
I recently decided that I didn't want to use windows anymore due to a variety of reasons, however I have been booting ubuntu from an external HD for quite some time. Is there a way I can copy ubuntu from my external HD to my internal HD?

I would just use a live ubuntu cd using gparted or gparted live cd and copy and paste the partition from the external to the internal, this method keeps the external intact in case any mistakes are made. Same size or bigger partition on the internal is needed

You would just have to install grub to the mbr check out this link on a chroot to the ubuntu on the internal and installing grub.

[https://help.ubuntu.com/community/Grub2/Installing#ChRoot](https://help.ubuntu.com/community/Grub2/Installing#ChRoot)

You could also use clonezilla to clone the external then put on the internal, this would give you a back up as well. Again same or bigger size partition on internal

[http://clonezilla.org/](http://clonezilla.org/)

Some would offer a dd which is just a copy from to. Personally I would use a method that keeps the original or has a clone just to cover any possibility of failure.

---

