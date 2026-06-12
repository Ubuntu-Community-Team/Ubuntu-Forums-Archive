---
title: "not enough space to upgrade"
date: 2019-03-10
forum: Installation &amp; Upgrades
---

### Post by drupstone on 2019-03-10
Who can help me out? I have a upgrade standing but not enough space, I did clean up with apt-get but that is not enough ,
now I get the advice to:     /etc/initramfs-tools/initramfs.conf   optie  compress=xz        but I do not know what to do with this message in order to make space

---

### Post by Impavidus on 2019-03-10
Maybe you just have to remove some old kernels. What do you get from these commands?```
df -h
df -i
dpkg --list | grep linux-
```

---

