---
title: "Ubuntu update from 11.04 to 11.10"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by editheraven on 2011-10-15
I have a couple of questions. After the update, my gnome settings and grub configuration will be reseted? Do i have to redo all gnome panels setup, nautilus settings etc? Also, 11.10 have backwards compatibility with all 11.04 installed packages? Are there any issues with nvidia driver and wine 1.2.2?

---

### Post by 2F4U on 2011-10-15
Your grub settings should remain the same, but your gnome settings may change. Read the different reports about upgrading here on the forum and you will see that different people report different experiences about upgrading. With respect to backwards compatibility it is certain that not all installed packages are backwards compatible. On my Xubuntu install, 31 packages were obsolete after the upgrade and I choose to remove these packages.

---

### Post by raja.genupula on 2011-10-15
> **editheraven said:**
> I have a couple of questions. After the update, my gnome settings and grub configuration will be reseted? Do i have to redo all gnome panels setup, nautilus settings etc? Also, 11.10 have backwards compatibility with all 11.04 installed packages? Are there any issues with nvidia driver and wine 1.2.2?

```
lsmod | grep video
```
gonna gives information about your graphics driver status.I think there is no problem for wine tools from 11.10.

all the best.

---

