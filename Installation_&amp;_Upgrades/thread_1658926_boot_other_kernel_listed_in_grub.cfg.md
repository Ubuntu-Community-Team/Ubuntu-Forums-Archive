---
title: "boot other kernel listed in grub.cfg"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by egerlach on 2011-01-03
Im running lucid 10.04 and want ubuntu to boot as default a older kernel listed in /boot/grub/grub.cfg. Where can I change the default setting?

thx
Eckard

---

### Post by matt_symes on 2011-01-03
Hi

Install startupmanager

```
sudo apt-get install startupmanager
```

or install it from synaptic and change the kernel you boot into from there. That's the easiest way.

Kind regards

---

