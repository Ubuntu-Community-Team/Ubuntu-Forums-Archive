---
title: "Software RAID, Partition Resize, 1st OS gone"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by MartinChir on 2010-03-23
I had Ubuntu install fine with software RAID, I installed another distro thinking it would install onto the free 12GB partition instead it seems to have resized the RAID Ubuntu partition & now my Ubuntu installation is not present on GRUB, just the new distro loads.


I had important school work that I need, can anyone help?

---

### Post by MartinChir on 2010-03-24
I managed to open a shell into the original RAID partition, it's preserved with all the files.

So I tried deleting & remaking the grub2 bootloader, it worked however it only picks up the BT4 distro! So any ideas?

---

### Post by MartinChir on 2010-03-25
Copied files from recovery shell; mounted USB HDD, changed permissions, used cp -R.

That's all folks...

No thanks to Peter :-P

---

