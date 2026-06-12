---
title: "How to prevent Update Manager from installing grub?"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by Piscium on 2009-11-15
I was having problems with Grub2 on Karmic, so uninstalled it, got the sources from the Grub website, built it, and it works well.

Unfortunately the kernel update (2.6.31-15) caused grub-pc and grub-common to be reinstalled, so I had to manually uninstall them.

Is there a way to prevent Update Manager from installing grub-pc and grub-common the next time there is a new kernel available?  Some APT command?

Thanks in advance.

---

