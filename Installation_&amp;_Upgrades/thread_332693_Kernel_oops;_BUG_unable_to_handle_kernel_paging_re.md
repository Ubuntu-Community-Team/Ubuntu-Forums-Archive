---
title: "Kernel oops; BUG: unable to handle kernel paging request at xxxxxxxx"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by BsAtHome on 2007-01-06
Hi,

I've been trying to install 6.10 on a clean system. The install consistently results in a kernel oops with the message:
BUG: unable to handle kernel paging request at xxxxxxxx

The same problem occurs with fedora 4, 5 and 6. So I started to investigate the hardware a bit more. When I remove the PCI-Express graphics card (NVidia 6200GT), then all works fine with the onboard i915 chipset. So I guess that there is a problem in the kernel's PCI express handling. I've seen quite some messages scattered about similar oopses. Any suggestions how to proceed?

--
Greetings Bertho

---

