---
title: "error processing linux-image-2.6.31-16-generic"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by spufidoo on 2009-12-07
Hi. Update-manager updated my kernels, but failed with this:

Setting up linux-headers-2.6.31-16-generic (2.6.31-16.52) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.31-16-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.31-16-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.31-16-generic (2.6.31-16.52) ...
Running depmod.

Any clues? I seem to boot into 2.6.31-16 OK.

---

