---
title: "Ubuntu 22.04 does not boot with kernel 6.2.0-31-generic"
date: 2023-09-01
forum: Installation &amp; Upgrades
---

### Post by Genom on 2023-09-01
I was getting a black screen during boot process on my Lenovo L490. I was able to boot with the other saved kernel 6.2.0-26-generic through the GRUB menu.

I wonder, what went wrong there.

---

### Post by ubfan1 on 2023-09-01
Maybe a video driver problem. Do you have Nvidia hardware?  Can you switch to a virtual terminal (ctrl+alt+Fn3) and login?  If you get in, try the sudo apt update and upgrade again and note if any packages are being held back.  I have seen a video package held back by phasing and the driver refused to build for the new kernel.  Waited a day, and then the upgrade worked (from a previous kernel).

---

### Post by lw1at on 2023-09-05
I get the same problem on a Lenovo L590 (which I think is identical apart from the screen size).
apt doesn't show any updates and I am not sure if this is video driver related. When picking the linux image in GRUB instead of seeing the kernel log after a few seconds when booting on 6.2.0-26, it is already stuck after "Loading initial ramdisk" when using 6.2.0-31.

I think this might be describing the same issue (but on the 5.15 branch):

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2032173](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/2032173)

---

