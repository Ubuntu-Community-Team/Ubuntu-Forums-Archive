---
title: "creating a new partition out of swap space"
date: 2006-04-15
forum: Installation &amp; Upgrades
---

### Post by binilbenjamin on 2006-04-15
i'm having a machine with 1gb RAM....when i installed ubuntu , i kept apart 1gb for swap space....is this necessary??? moreover, i have winxp installed in the machine with all file system to be NTFS. could i create a new partition in swap space (with FAT32 fs) for about 300mb, so tht i could easily r/w in both win&linux??? will creating a new partition create any mess in the already installed ubuntu??

---

### Post by aysiu on 2006-04-15
You can create a new FAT32 partition out of swap.

You may have to use a live CD for this, though, as I believe swap is "mounted" while you're using Ubuntu.

Try something like GParted, which can be installed through apt-get or Synaptic.

---

