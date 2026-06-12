---
title: "error 13"
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by glennnf on 2008-06-30
HI Guys,i disconnected my slave(ubunntu)to see if my master(vista) would boot,no luck,so i reconnected slave & now im getting "error 13" invalid or unsupported exe format,any ideas?Thanks.

---

### Post by VMC on 2008-07-01
> **glennnf said:**
> HI Guys,i disconnected my slave(ubunntu)to see if my master(vista) would boot,no luck,so i reconnected slave & now im getting "error 13" invalid or unsupported exe format,any ideas?Thanks.

When you say disconnected. Was this an internal hard drive or external. What prompted you to disconnect it in the first place? Was it not booting correctly?

Plug everything in the way you want it and from a Terminal type the following:

```
sudo fdisk -l
```

---

### Post by ajopaul on 2008-07-01
looks like the MBR is out, use a bootable cd, to rebuild the grub..

---

