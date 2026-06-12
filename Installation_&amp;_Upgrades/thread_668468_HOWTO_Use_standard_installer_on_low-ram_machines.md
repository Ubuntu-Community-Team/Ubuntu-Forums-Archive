---
title: "HOWTO: Use standard installer on low-ram machines"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by steevols on 2008-01-15
I recently succeeded in installing Ubuntu on a 500mhz 128MB ram laptop with the standard LiveCD! If you have an external hard-drive or a flash drive, you can use them as swap-space, ala Vista's ReadyBoost (or whatever it's called.)

1.Boot Live CD
2. Switch to terminal (I.E., CTRL+ALT+F1)
3. ```
cd /media/nameofdisk
```
4. ```
dd if=/dev/zero of=swap bs=1M count=200
```
5. ```
mkswap swap | swapon swap
```
6. Return to desktop (CTRL+ALT+F7)
7. Install as usual

Handy way to install if you don't have the alternate-cd downloaded at the time.

---

