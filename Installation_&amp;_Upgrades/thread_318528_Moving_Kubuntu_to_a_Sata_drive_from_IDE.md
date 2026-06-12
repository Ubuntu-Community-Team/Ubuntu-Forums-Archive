---
title: "Moving Kubuntu to a Sata drive from IDE"
date: 2006-12-14
forum: Installation &amp; Upgrades
---

### Post by NZ-Wanderer on 2006-12-14
Hi all, I've become rather stuck.. - Today I bought a nice brand new sata drive, installed Vista (need it for games) in the first partition, and then copied my Kubuntu root, Home, swap partitions over to the Sata drive in exactly the same order I had them on the ide drive...

Now, Vista is on the first partition, Kubuntu root is on the second partition, home on the third  and so on...

Is there any way of me setting the boot sector of the second partition of my sata drive without having to reinstall Kubuntu again please?? (I forgot when I used Acronis partitioner to copy the partitions that it wouldn't copy the boot sectors on the second partition.)

Any help would be appreciated...

---

### Post by adwait on 2006-12-14
Umm....you could boot off the live CD and install GRUb with
```
sudo grub-install /dev/sda
```

That should work .... I think...

---

### Post by NZ-Wanderer on 2006-12-14
Thanks for the reply, I will give that a go :) :)

> **adwait said:**
> Umm....you could boot off the live CD and install GRUb with
```
sudo grub-install /dev/sda
```
That should work .... I think...

---

