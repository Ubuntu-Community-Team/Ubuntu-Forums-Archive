---
title: "Intel driver wont load."
date: 2013-08-24
forum: Installation &amp; Upgrades
---

### Post by petterjohansson333msn.com on 2013-08-24
hello I have this problem that my intel driver wont load and im not sure whats causing it.

I have changed my grub to fix my black screen problem:
GRUB_CMDLINE_LINUX="i915.modeset=0"
is that what might cause it?
I have no xorg.config

I installed the latest intel driver
I've been searching around trying to figure it out but I have no clue how to do next...

not sure what info you need to help but.

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Haswell Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller cap_list
       configuration: latency=0
       resources: memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)

Graphics: Gallium 0.4 on llvmpipe (LLVM 3.2, 256 bits)

---

### Post by Crusty Old Fart on 2013-08-26
The following entry in your grub disables kernel modesetting for the default i915 driver:
```

GRUB_CMDLINE_LINUX="i915.modeset=0"

```
Please try the following line in your grub instead of the one above and let me know what happens:
```

GRUB_CMDLINE_LINUX="i915.modeset=1"

```
Before we create an xorg.confg file, I also need to know what operating system you're running.

---

### Post by Crusty Old Fart on 2013-08-28
Bump after rewriting post #2.

---

