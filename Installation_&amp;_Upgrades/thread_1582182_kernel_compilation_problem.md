---
title: "kernel compilation problem"
date: 2010-09-26
forum: Installation &amp; Upgrades
---

### Post by dulan2010 on 2010-09-26
I have installed ubuntu 10.4 using VMware under windows 7 on my mackbook, I tried to compile the kernel since I want to add some kernel modules into it, so I get linux-2.6.35.5.tar.bz2 from kernel.org, untar it into /usr/src, some necessary procedures blah blah blah, then when I type in:
make-kpkg --initrd --append-to-version=-linux-2.6.35.5-image
I get this error:
arch/x86/Kconfig: 2095 can't open file "ubuntu/Kconfig"
 
and the compilation fails, how'd this happen? any help? Thanks in advance!

---

