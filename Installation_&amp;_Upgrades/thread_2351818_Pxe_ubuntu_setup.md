---
title: "Pxe ubuntu setup"
date: 2017-02-07
forum: Installation &amp; Upgrades
---

### Post by michele.123456 on 2017-02-07
I want to install ubuntu desktop via HTTP.
I unpacked the 14.01 desktop iso in a folder on the http, configured the pxe with the pxelinux.cfg needed files.(read in many threads) created the pressed file with the
d-i live-installer/net-image=http//....
and passing at the kernel params the same param live-installer/net-image.
Then I PXE booted the target machine initrd.lz and vmlinux.efi are loaded but it ends up in the initramfs looping for /dev/sr0.
I just wandering if it's possible to do that.
Thanks

---

