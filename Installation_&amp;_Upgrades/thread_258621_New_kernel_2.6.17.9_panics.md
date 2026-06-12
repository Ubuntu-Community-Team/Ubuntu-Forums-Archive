---
title: "New kernel 2.6.17.9 panics"
date: 2006-09-16
forum: Installation &amp; Upgrades
---

### Post by drange on 2006-09-16
After upgrading to the latest kernel, my laptop goes to kernel panic.

```
title       Ubuntu, kernel 2.6.17.9 Default
root        (hd0,0)
kernel      /boot/vmlinuz root=/dev/hda1 ro quiet splash
savedefault
boot
```

The one that works:```
title       Ubuntu, kernel 2.6.15-26-386
root        (hd0,0)
kernel      /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd      /boot/initrd.img-2.6.15-26-386
savedefault
boot
```Any ideas? I believe it can have something to do with my IPW2200...

---

