---
title: "I actually installed a 32-bit kernel to a 64-bit system - Please help"
date: 2011-12-09
forum: Installation &amp; Upgrades
---

### Post by unckybob on 2011-12-09
I was trying to install an older kernel to a system and ran

sudo dpkg -i linux-image-2.6.38-02063808-generic_2.6.38-02063808.201106040910_i386.deb

on a 64-bit system. Can someone please tell me how to undo it?

---

### Post by MAFoElffen on 2011-12-09
> **unckybob said:**
> I was trying to install an older kernel to a system and ran

sudo dpkg -i linux-image-2.6.38-02063808-generic_2.6.38-02063808.201106040910_i386.deb

on a 64-bit system. Can someone please tell me how to undo it?
```

sudo apt-get remove --purge linux-image-2.6.38-02063808-generic_2.6.38-02063808.201106040910_i386

```

---

### Post by 73ckn797 on 2011-12-09
You can use Synaptic also. Look for the version under linux. There will be 3 entries designating that. Actually fairly easy if they show up there. I have never installed a kernel using a deb pkg.

---

### Post by MAFoElffen on 2011-12-09
> **73ckn797 said:**
> You can use Synaptic also. Look for the version under linux. There will be 3 entries designating that. Actually fairly easy if they show up there. I have never installed a kernel using a deb pkg.
FYI- Looks like he did "mainline PPA"... and those are the install instructions they have posted there...

---

### Post by unckybob on 2011-12-10
I used synaptic. Thanks so much, it was easy.

---

