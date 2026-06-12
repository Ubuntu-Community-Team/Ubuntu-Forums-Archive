---
title: "Swap partition locked?"
date: 2010-08-03
forum: Installation &amp; Upgrades
---

### Post by icarus035 on 2010-08-03
Hi all. I have Ubuntu 10.04 installed. When I run Ubuntu 10.04 LiveCD and I start GParted I see that there is a "key" on my swap partition marking it as locked I guess. When I right click, I cannot select "Delete" option. What does this mean? What if I want to rearange my partitions sizes including swap partition for whatever reason?
Thanks in advance.

---

### Post by lechien73 on 2010-08-03
The "lock" icon means that your swap partition is mounted, that's why you can't modify it.

In GParted you can right click on the swap partition and select "Swapoff". This will disable the swap partition so you can delete or resize it.

---

