---
title: "[SOLVED] help in adding kernel 2.6.24.18 to grub menu"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by nantax on 2008-06-04
I have finished downloading the new kernel and during the update process I mistakenly chosen to keep the old grub menu. The new kernel appears in synaptic but does not appear in the grub boot menu.

How do I add it manually to the grub boot menu list?

-----

Bazhang helped me in the IRC channel.
I just renamed the old menu.lst file from /boot/grub directory and ran sudo update-grub.

---

