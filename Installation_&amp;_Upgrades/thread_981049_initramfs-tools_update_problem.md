---
title: "initramfs-tools update problem"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by delta-delta on 2008-11-13
[FONT="Tahoma"]Hi all,

I have recently setup ubuntu server 6.06 LTS on a Dell poweredge 2450. I used 6.06 because for some strange reason no new version of ubuntu would boot. 

I recently upgraded the distribution, but found my /boot partition was nearly full, so the upgrade exited somewhere near the end. I freed some space up and then ran the update command, and got this:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the poblem
```

So I ran this and this is what followed:

```
Setting up initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...update-initramfs: Generating /boot/initrd.img-2.6.24-21-server
cpio: ./sbin/vgchange: Cannot stat: No such file or directory
```

I googled this and found [HTML]http://lists.alioth.debian.org/pipermail/pkg-lvm-maintainers/2007-April/001095.html[/HTML]

The only problem is, I have no idea what this means. Can anyone help me fix this please?

Thanks in advance :)

[/FONT]

---

### Post by nesono on 2010-01-27
It can be so simple - simple call the following command:
```
sudo dpkg --purge lvm-common
```and upgrade your system as usual afterwards.

---

