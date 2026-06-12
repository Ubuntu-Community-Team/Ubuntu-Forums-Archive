---
title: "Attempting to install ubuntu-22.04.2-live-server-amd64 on AMD FX-6100 system."
date: 2023-06-26
forum: Installation &amp; Upgrades
---

### Post by wyckedjester on 2023-06-26
Hello all!  I'm attempting to install Ubuntu via a flash drive with ubuntu-22.04.2-live-server-amd64.iso on it on a system with an AMD FX-6100 processor.  It hangs every time I attempt it and the last time I saw a message which appears to indicate this processor is no longer supported (yeah, the processor is a bit old).  Anyone know how to get around this problem or what the latest version of Ubuntu was that I could use?  Many thanks in advance!!

---

### Post by MAFoElffen on 2023-06-26
On my workstation running Ubuntu 22.04.2:
```

mafoelffen@opti-ubuntu:~$ grep -i "name" /proc/cpuinfo | head -n 1
model name    : AMD Opteron(tm) Processor 6386 SE

```
It came out in 2012 and has similar arch. I have no problems. My workstation previous to that one was AMD FX-60 (2006), which I owned through Ubuntu 16.04 LTS before retiring it.

Do this... Booting from the 22.02.2 Server LiveUSB, at the Grub2 boot menu, press the <E> key to go into an edit mode. <Arrow-Down> until you get to the line that starts with "linux". <Arrow-Right> until you get to "---". After that, add "3  --verbose debug drm.debug=0xe plymouth:debug". Press <Cntrl><X> to continue the boot.

Watch the output for clues... Maybe video it with your phone, so you can revie

---

