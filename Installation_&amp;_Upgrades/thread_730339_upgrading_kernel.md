---
title: "upgrading kernel"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by bamboomy on 2008-03-20
Hi 'yall,

everytime a kernelupdate is available the update resets my menu.lst to root (hd0,0) and root=/dev/hda1 whilst my ubuntu resides on (hd0,2) and thus root=/dev/sda3 like this:

```

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

```

although this is nothing more then annoying it seems like a problem that can easily be fixed without setting the values right manually every time...

is there an easy fix ?

tnx for answers,

S.

---

