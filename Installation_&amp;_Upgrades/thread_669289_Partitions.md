---
title: "Partitions"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by mschraier on 2008-01-16
I have a 60GB drive partitioned basically in half between XP & Ubuntu with a small Linux Swap file.  Ubuntus partition is the 2nd one.  Can I resize or shave part of that off so I can do a complete Kubuntu install?  I had both desktops installed but it didnt quite work out.  SO i want to do a separate install.  Can this be done?  Willthat create an triple boot in Gurb?  The dual boot and Ubuntu are working great.

---

### Post by milton1 on 2008-01-16
yes, you can easily fit the kubuntu install on 5 GB. (though I would recommend a bit more, just for wiggle room) You can also reuse the swap partition.

---

### Post by rsambuca on 2008-01-16
Yes, you can use either an K/Ubuntu liveCD, or something like the gParted live CD to shrink your existing partition and add another for Kubuntu.  As the previous poster suggested, I would just share the swap between the two *buntus.

---

### Post by mschraier on 2008-01-16
I opened gparted to try.  however, all the partitions had locked locks next to them.  resize was not an option only unmount and properties.  any ideas????

---

### Post by rsambuca on 2008-01-16
> **mschraier said:**
> I opened gparted to try.  however, all the partitions had locked locks next to them.  resize was not an option only unmount and properties.  any ideas????

If you want to resize your existing Ubuntu partition, then you have to use a live CD.  You can't work on a partition that is already mounted.  That is why I suggested one of the liveCD's.

---

