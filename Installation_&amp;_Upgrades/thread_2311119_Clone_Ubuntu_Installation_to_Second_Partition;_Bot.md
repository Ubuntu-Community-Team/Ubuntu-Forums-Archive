---
title: "Clone Ubuntu Installation to Second Partition; Both Partitions Bootable"
date: 2016-01-24
forum: Installation &amp; Upgrades
---

### Post by fixitwolfe7 on 2016-01-24
Hello, I have 64-bit Ubuntu Server 14.04.3 LTS installation running from a single 500GB partition. I need to split this partition into two 250 GB partitions, clone the Ubuntu installation to the second, and have both installations bootable from GRUB separately. Is this possible? If so, how do I go about accomplishing this?

Thank you in advance. :D

---

### Post by Nuno_Abreu on 2016-01-25
To clone, you better boot from a Live-CD. After that, run into a Terminal and do this (don't forget to split the partitions first):
```
sudo rsync -av --progress /path/to/source/ /path/to/destination/
```

After that, on the Terminal still:
```
sudo chroot /path/to/destination/ && sudo update-grub
```

It could have conflicts, but it should be fine.
Tell me the results!

---

### Post by fixitwolfe7 on 2016-01-25
That was it! Thank you!

---

### Post by Nuno_Abreu on 2016-01-25
Did it work? Great!

---

