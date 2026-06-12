---
title: "Upgrade to 12.04 on a system with LVM failed"
date: 2012-06-12
forum: Installation &amp; Upgrades
---

### Post by MatsSoderhall on 2012-06-12
I have spent a whole day with upgrading to 12.04 on my computer with raid+lvm and want to share some of my findings...

After upgrading to 12.04 the computer hangs with a purple screen directly after selecting kernel in the GRUB-menu.

It turned out that the issue was that when upgrading to kernel 3.x, the modules needed for accessing LVM was not updated.

I managed to boot with kernel 2.6, but the system was very unstable (VGA-resolution, no mouse, sometimes no keyboard...). But it did allow me to run a terminal:
```

>sudo apt-get install lvm2
>sudo apt-get install mdadm
>sudo reboot

```
This is how simple it was in the end...

---

