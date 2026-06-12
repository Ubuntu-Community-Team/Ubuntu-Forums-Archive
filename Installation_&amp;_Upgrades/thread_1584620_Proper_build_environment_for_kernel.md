---
title: "Proper build environment for kernel"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by macaddict01 on 2010-09-29
Hi folks. First time posting here but a long time reader of all this valuable information!

Wondering if anyone can tell me what piece of the puzzle I'm missing here. I'm building my 2.6.3x kernels from kernel.org on a regular basis with the following simple method-

```
make clean mrproper
make oldconfig && make prepare
make xconfig
make -j5 && make modules_install
make headers
make install
update-grub
```

My problem seems to be that lots of software such as VMware, Vbox, PulseAudio, etc always complains about some sort of improper build environment. Ultimately DMS tries to build module(s) and always fails. Is this typically because it's unable to find my source and/or headers? My source is in /home.

Am I missing a command in my build process that allows DKMS to be aware of the source and headers? Any insight is much appreciated.

---

