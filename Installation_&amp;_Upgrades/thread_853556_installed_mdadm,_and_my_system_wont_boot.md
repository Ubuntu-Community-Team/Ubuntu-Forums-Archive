---
title: "installed mdadm, and my system wont boot"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by lunxer on 2008-07-08
I  installed mdadm via apt-get install mdadm and after a reboot grub output something like this.

```
VFS: Cannot open root device "sda1" or unknown-block(0,0)
Please append a correct "root=" boot option
```

I have tried to remove mdadm via a live env. but i dont think its working, 

```
/boot/initrd.img-2.6.18-5-486 has been altered. Cannot update.
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: ----------------------------------------------------
invoke-rc.d: WARNING: invoke-rc.d called during shutdown sequence
invoke-rc.d: enabling safe mode: initscript policy layer disabled
invoke-rc.d: ----------------------------------------------------

```

I would appricate ANY ideas!

---

