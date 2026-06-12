---
title: "[SOLVED] Upgrade from 7.10 to 8.04 - no 7.10 in grub"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by Kevbert on 2008-10-28
I've just performed a distribution upgrade via Upgrade Manager from 7.10 to 8.04.  My grub menu.lst file no longer shows 7.10 only 8.04.1, but one of the kernels displayed is still 2.6.22.15.  Does this mean that I can no longer use 7.10 ?
My menu.lst file boot options:
```
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=4396a47e-3906-48d3-965f-51762e074a5d ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=4396a47e-3906-48d3-965f-51762e074a5d ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.22-15-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=4396a47e-3906-48d3-965f-51762e074a5d ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=4396a47e-3906-48d3-965f-51762e074a5d ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet
```

---

### Post by snowpine on 2008-10-28
You can install 7.10 and 8.04 on separate partitions and double boot if you want to use both (not sure what the advantage would be). Doing a dist-upgrade switches all of your installed packages over to the newer versions.

You can boot using the old kernel if you want. This is often very useful when troubleshooting hardware problems, for example. The difference between using the 7.10 kernel in 8.04 vs. using the 7.10 kernel in a 7.10 install is the package versions. For example, your Firefox should now be FF3 instead of FF2, regardless of which kernel you boot with.

Hope that clears things up somewhat!

---

### Post by Kevbert on 2008-10-28
Thanks snowpine for clearing that up.  The PC in question is my laptop and it has limited disk space so two separate partitions for Ubuntu is not an option.

---

