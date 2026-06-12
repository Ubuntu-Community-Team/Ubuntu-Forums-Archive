---
title: "Cannot install linux-headers-2.6.20-16.35"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by noup on 2008-04-26
I'm getting the following error in Synaptic when trying to update linux-headers-2.6.20-16.32 to linux-headers-2.6.20-16.35:

```
(Reading database ... 142109 files and directories currently installed.)
Preparing to replace linux-headers-2.6.20-16 2.6.20-16.32 (using .../linux-headers-2.6.20-16_2.6.20-16.35_i386.deb) ...
Unpacking replacement linux-headers-2.6.20-16 ...
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.20-16_2.6.20-16.35_i386.deb (--unpack):
 unable to stat `./usr/src/linux-headers-2.6.20-16/include/asm-sparc64/mman.h' (which I was about to install): Permission denied
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-2.6.20-16_2.6.20-16.35_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```

This is under Feisty. I'm finishing remaining updates so I can then upgrade to Gutsy and Hardy. Any help?

---

