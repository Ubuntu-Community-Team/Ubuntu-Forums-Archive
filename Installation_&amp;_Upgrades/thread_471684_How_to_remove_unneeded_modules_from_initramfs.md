---
title: "How to remove unneeded modules from initramfs?"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by EmmEff on 2007-06-12
Is it possible to disable unneeded modules from loading at boot?

I tried using the MODULES=list option in /etc/initramfs-tools.conf and listing modules in /etc/initramfs-tools/modules but it still includes stuff I don't want (like vesafb and fbcon).

What is the proper way of disabling this?  The installation is for a server and I don't need framebuffer support on the console, agpgart, the floppy driver, and a bunch of other modules that load by default but aren't needed.

Any hints?  Thanks.

---

