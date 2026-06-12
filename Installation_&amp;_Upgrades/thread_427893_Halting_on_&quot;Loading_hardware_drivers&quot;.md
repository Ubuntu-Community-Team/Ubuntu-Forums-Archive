---
title: "Halting on &quot;Loading hardware drivers&quot;"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by r!ots on 2007-04-29
hey guys,

today I updated to fiesty fawn. The upgrade process itself worked flawlessly, but when I restarted my PC as prompted it halted upon loading hardware drivers and started flashing two keyboard lights.
I then rebooted in recovery mode but again it crashed when trying to load the hardware drivers.
I got the following output:

```
floppy0: sensei repl[0]=80
floppy0: unexpected interrupt

```
Does anybody have any idea how to fix that?

I then booted in the old kernel (2.6.17-11-386) where I got past the point where it crashed before but the X server didn't start. I got the following error message:

```
Error: API mismatch:
the NVIDIA kernel module has the version 1.0-8776, but this X module has the version 1.0-9631.
Please make sure that the kernel
module and all NVIDIA driver components have the same version.
```

Now I'm running the nv-drivers and if I try to use the NVIDIA-drivers the X server crashes again. Any ideas how to fix that one?

Thx for your help.

---

