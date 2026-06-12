---
title: "nvidia driver"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by Lagos on 2007-12-03
I just installed a fresh copy of Gutsy and enabled the Nvidia restricted driver. Should I upgrade to the NVIDIA-Linux-x86-100.14.19 driver, or keep the restricted one? How can I even find out what version of the Nvidia driver I have?

---

### Post by TSJason on 2007-12-03
Hi Lagos,

 IMO don't upgrade if everything is working properly. Bleeding edge isn't necessarily always the best. That said, you should be able to see what version of the driver that is being loaded from a shell. Run:

```
dmesg |grep -i nvidia
```

---

### Post by Lagos on 2007-12-03
Everything is working great, except that firefox scrolling is a lot slower then it normally is in XP. I was hoping maybe a new version of the driver would address that.

---

