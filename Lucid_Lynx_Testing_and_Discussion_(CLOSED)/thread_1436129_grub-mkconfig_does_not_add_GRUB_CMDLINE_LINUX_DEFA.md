---
title: "grub-mkconfig does not add GRUB_CMDLINE_LINUX_DEFAULT parms to all entries"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ubername on 2010-03-22
Hi

I have
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1"

in etc/default/grub file

This is added to all the options added from 10_linux in grub.cfg but not to linux variants found by 30_os-prober.

Is this to be expected? If so, how can I add this (I guess I can use 40_custom, but is there another way?)

---

