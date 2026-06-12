---
title: "Executing 'grub-install /dev/sda' failed"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by Jagot on 2011-05-20
I've been trying to install Natty (64) over the last couple of weeks and am having problems that I've never had with any distribution before.  At the end of each install, I get the following error:

```
Executing 'grub-install /dev/sda' failed
```

It then gives me the option of installing grub somewhere else, which I don't want, but it doesn't work anyway, or leaving without a boot loader, which isn't really desirable.

At first I thought it might be something to do with my previously complicated quad-boot partition layout, so I simplified that to a fairly regular Windows and Ubuntu only, but no luck.

Grub also fails when attempting to upgrade 10.10.

I've tried restoring Grub2 using chroot amongst other things which doesn't work.

Any ideas what's going on here?

---

### Post by Dutch70 on 2011-05-20
Have you tried running...
```
sudo grub-install --recheck /dev/sda
```

---

