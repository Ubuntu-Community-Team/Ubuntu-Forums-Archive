---
title: "Safe to run Windows (XP) Defragmentation after WUBI install?"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by hyperation on 2011-02-27
Hello,

I am fairly new to Ubuntu (and Linux in general).  Recently, I installed Ubuntu 10.10 without defragmenting my hard drive first (newbie mistake).  So now the root.disk and swap.disk file are very fragmented (45k and 2.4k pieces).  I am wondering is it safe to do a Windows defragmentation right now?

Thanks
:)

---

### Post by bcbc on 2011-02-27
Yes it's safe, but defrag will probably ignore large files like the root.disk (it gives a report at the end saying "The following files could not be moved"). If that happens you can try moving the root.disk on to an external drive before defragging, and then copying it back afterwards. I've done this before without ill-effect, but to be safe backup important data that you have on Ubuntu off the root.disk to the /host partition.

---

### Post by hyperation on 2011-02-27
> **bcbc said:**
> Yes it's safe, but defrag will probably ignore large files like the root.disk (it gives a report at the end saying "The following files could not be moved"). If that happens you can try moving the root.disk on to an external drive before defragging, and then copying it back afterwards. I've done this before without ill-effect, but to be safe backup important data that you have on Ubuntu off the root.disk to the /host partition.

Cools, thanks for the response.

---

