---
title: "Kernel RT on lucid lynx"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by dcuder on 2010-04-30
Both in 32 and 64 bit I cannot boot kernel-rt.
Message displayed: mounting none on /dev failed: no such device
Then get login message in text console, gdm cannot start.

Any suggestion? Thanks a lot

---

### Post by dcuder on 2010-05-06
SOLVED!
I answer myself..... It was a graphic card problem... With new open nvidia drivers, you must load the correct driver for each kernel you're going to boot.
So I've installe heders and source for 2.6.31 and then I booted the terminal mode of kernel 2.6.31-rt and run the nvidia driver downloaded from nvidia.com, e.g.
# sh NVIDIA-Linux-x86_64-195.36.24-pkg2

---

