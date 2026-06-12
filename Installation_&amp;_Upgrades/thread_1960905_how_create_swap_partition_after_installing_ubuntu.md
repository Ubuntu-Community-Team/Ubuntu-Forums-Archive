---
title: "how create swap partition after installing ubuntu"
date: 2012-04-18
forum: Installation &amp; Upgrades
---

### Post by fire planet on 2012-04-18
hi,
i installed 32 bit version of ubuntu 11.10 recently. during installation i enterde manual partitioning . i installed ubuntu without setting a partition for swap area (just set the root partition).
now please tell me  is it necessary to have a swap partition?
and if yes, how should i create a swap area now?

---

### Post by nothingspecial on 2012-04-18
Hi, it might be easier to create a swap file.

Read this

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by kurt18947 on 2012-04-18
> **nothingspecial said:**
> Hi, it might be easier to create a swap file.

Read this

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Yup.  The only downside (and it isn't for me) is that a swap **partition** is required to be able to hibernate or suspend-to-disk.  From what I've read, resuming from hibernation is not much faster than a cold boot so i don't worry about it.  I either suspend (to RAM) or shut down.  Create a swap partition if you feel the need.  I have 4 GB RAM and haven't even come close to using it all so don't feel the need for swap.  The only time I could see me needing swap would be running one or more virtual machines, each with open apps.

---

### Post by fire planet on 2012-04-19
> Yup.  The only downside (and it isn't for me) is that a swap **partition**  is required to be able to hibernate or suspend-to-disk.  From what I've  read, resuming from hibernation is not much faster than a cold boot so i  don't worry about it.  I either suspend (to RAM) or shut down.  Create a  swap partition if you feel the need.  I have 4 GB RAM and haven't even  come close to using it all so don't feel the need for swap.  The only  time I could see me needing swap would be running one or more virtual  machines, each with open apps.
thank you :)
with your explanation now i think swap area is not necessary for me :D

---

### Post by fire planet on 2012-04-19
> **nothingspecial said:**
> Hi, it might be easier to create a swap file.

Read this

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

thank you :)

---

