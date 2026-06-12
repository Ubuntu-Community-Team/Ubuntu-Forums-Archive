---
title: "Major upgrade headaches, permissions set wrong?"
date: 2006-07-22
forum: Installation &amp; Upgrades
---

### Post by chevling on 2006-07-22
only.

---

### Post by mlind on 2006-07-22
Are you able to mount your root partition and chroot it?

Find your root partition
```

sudo fdisk -l

```

Then create mount point for it and try to mount
```

sudo mkdir /mnt/root
sudo mount /dev/xxx /mnt/root

```

```

sudo chroot /mnt/root /bin/bash

```

---

### Post by chevling on 2006-07-25
:

---

