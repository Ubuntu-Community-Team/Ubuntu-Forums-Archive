---
title: "dual boot install, 12.04"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by pratikk on 2012-04-26
I want to freshly install 12.04 on two machines which already run Linux dual boot with Win. One runs Ubuntu 10.10, the other Bodhi. Do I just boot from the 12.04 CD, point to the Linux partition and Grub is automatically updated on install, or is manual editing required? Just want to be sure.

Thanks

Pratik

---

### Post by darkod on 2012-04-26
To install over existing linux? No grub2 editing is needed.

However, you will have to use the manual partitioning and tell it to use the existing partition. It doesn't overwrite partitions by itself.

---

### Post by pratikk on 2012-04-26
Sure, I'll do that. Thanks a lot.

---

