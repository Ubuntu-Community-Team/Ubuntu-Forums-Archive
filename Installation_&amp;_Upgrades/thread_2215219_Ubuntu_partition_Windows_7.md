---
title: "Ubuntu partition Windows 7"
date: 2014-04-05
forum: Installation &amp; Upgrades
---

### Post by abby4 on 2014-04-05
I just got Ubuntu 13.10. I booted but when I get to installing it asks if i want to replace windows or something else. I click on something else but dont know what else to do. How do i partition ubuntu and Windows 7?

---

### Post by fantab on 2014-04-05
Post a screenshot of your HDD and its partitions from 'Windows Disk Management'.
Boot with Ubuntu DVD/USB and "Try Ubuntu (Without Installing), open Terminal [ctrl+alt+T]- run the following commands and post its output here:
```
sudo parted -l
sudo fdisk -l
```

---

### Post by Mark Phelps on 2014-04-05
> it asks if i want to replace windows or something else

That's most likely because, if your PC came with Win7 preloaded, it probably has already used up 4 partitions, and thus, the installer can not create any more.

The commands that fantab asked you to run will show us what partitions are on your drive.

---

