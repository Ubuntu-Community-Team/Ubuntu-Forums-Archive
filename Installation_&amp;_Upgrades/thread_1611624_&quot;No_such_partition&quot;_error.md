---
title: "&quot;No such partition&quot; error"
date: 2010-11-02
forum: Installation &amp; Upgrades
---

### Post by mistako on 2010-11-02
Good day.

I'm trying to install 10.10 to HP nw8440, it boot's from cd, installs and don't start's, just showing me "No such partition" error.

Partitions on my laptop are:
```
sda1 -> Win7 Bootloader
sda2 -> Win7
sda3 -> Ntfs partion
sda5 -> Ubuntu root partition
sda6 -> Swap
```

 Interesting is that grub rescue console on ls command shows me:
```
(hd0), (hd0,msdos3), (hd0,msdos2), (hd0,msdos1)
```
but in grub.cfg sda5 is written as (hd0,msdos5)

 Several times I tried to boot from livecd, chroot and run "update-grub", "grub-install" and other grub rescue commands with needed parameters, but there still "no such partition" error.

Please help!

P.S.: Please don't post links to grub rescue howtos, I read most of them, in my situation they are useless.

---

### Post by mistako on 2010-11-02
Still waiting for help

---

