---
title: "Windows Problems with installtion"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by Icenate001 on 2007-11-11
Hello my friend just installed ubuntu, he never uninstalled windows, so when he partitioned the hardrive, it always boots into ubuntu. It is telling him the windows partion is unformatted and therefore unaccessible. though he is telling me the information is still on there just inaccessiable is there anyway to recover that information.?? such as his documents and music.

---

### Post by forestpixie on 2007-11-11
can you get some information first and post it, in a terminal do these separately

```
sudo fdisk -l
cat /etc/fstab
cat /boot/grub/menu.lst
```

---

