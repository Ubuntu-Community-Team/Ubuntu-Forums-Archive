---
title: "Warning firmware /lib/firmware/i915/skl_guc_ver6.bin for module i915"
date: 2016-05-28
forum: Installation &amp; Upgrades
---

### Post by Nayab Basha Sayed on 2016-05-28
While building initramfs, I have encountered this warning. Is this safe to ignore? Why is this warning gererated?

```
me@linux:~/linux$ sudo mkinitramfs -o /boot/initrd.img-4.6.0+ 4.6.0+
W: Possible missing firmware /lib/firmware/i915/skl_guc_ver6.bin for module i915

```

---

### Post by dandart on 2016-06-03
The new Linux kernel now supports a later version of GUC, an Intel graphics firmware blob.

This is available at [https://01.org/linuxgraphics/intel-linux-graphics-firmwares](https://01.org/linuxgraphics/intel-linux-graphics-firmwares)

Download, extract and run install.sh, then reboot your machine to use it.

Cheers

---

