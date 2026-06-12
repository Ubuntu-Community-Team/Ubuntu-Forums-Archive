---
title: "making existing Feisty install to play with dm-crypto/luks"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by mlind on 2007-10-20
After installing Gutsy into encrypted LVM using alternative installer, I cloned my existing Feisty LV from another HDD inside the encrypted LVM. What are the steps to take to make Feisty booting work with this setup (luks) too ?

I guess I need to add a cryptab entry and probably load proper modules in /etc/modules? It seems that Gutsy loads necessary modules using initramfs hooks, but I dunno about feisty.

My setup is currently 

```

/dev/sda1 (/boot, unencrypted)
/dev/sda5 (LVM, encrypted)
  + (Ubuntu-root, Gutsy LV)
  + (Ubuntu-rootFeisty, Feisty LV)
  .
  .

```

---

### Post by mlind on 2007-10-20
nevermind, installing cryptsetup and adding a cryptab entry worked.

---

