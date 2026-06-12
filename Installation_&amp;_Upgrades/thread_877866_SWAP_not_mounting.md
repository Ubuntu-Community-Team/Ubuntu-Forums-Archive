---
title: "SWAP not mounting"
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by seanbarman on 2008-08-02
Hi,

My swap file does not start any more at boot!
The mount point keeps changing, it was originally set by uuid but was not starting after last wave of updates.
if i set it to /dev/sdf6 and mount it's ok but after a reboot
its changed to dev/sdb6! If i set to sdb6 it changes to sdf6!

i have added both to the fstab and it mounted last time, but surely this 
is not the norm.

---

### Post by cdtech on 2008-08-02
What do you get with:
```
sudo fdisk -l
```

And the:
```
sudo gedit /etc/fstab
```

---

