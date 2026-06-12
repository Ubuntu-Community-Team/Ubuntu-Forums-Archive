---
title: "Lucid rt kernel can't load latest nvidia driver module"
date: 2012-05-02
forum: Installation &amp; Upgrades
---

### Post by Marcod on 2012-05-02
Hello folks,

I'm on Lucid 10.04, got a Nvidia Quadro FX 880M, with proprietary driver.
I've just updated the nvidia driver to the 195.36.24 version, and the generic kernel headers to 2.6.32-41.
The updates came up with the Update Manager.

Now, this works good with the generic kernel, but when booting the rt kernel (still 2.6.31....) it fails to load the nvidia module.
I tried to load it manually, but it says it can't find it.

From what I learned on the forum, this might be because the new driver has been built against the new kernel, while the old rt kernel has now lost track of the nvidia module.

How to fix this?

many thanks in advance!

---

### Post by Marcod on 2012-05-02
ok, after looking at different threads, I eventually managed by:

1_ installing new rt kernel 2.6.33 from this PPA:
[https://launchpad.net/~bojo42/+archive/rt](https://launchpad.net/~bojo42/+archive/rt)

2_ installing "nvidia-graphics-drivers" from the PPA below, which is already patched to work with RT kernels:
[https://launchpad.net/~kxstudio-team/+archive/kernel](https://launchpad.net/~kxstudio-team/+archive/kernel)

Remember to run nvidia-xconfig once installed everything, and you're hopefully good!
Here works on both generic and RT kernels.

Many thanks to falkTX for his great work to tackle this issue.

---

