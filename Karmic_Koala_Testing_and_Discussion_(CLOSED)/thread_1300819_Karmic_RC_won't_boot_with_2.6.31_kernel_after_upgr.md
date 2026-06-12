---
title: "Karmic RC won't boot with 2.6.31 kernel after upgrade from Jaunty"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by topynate on 2009-10-25
After upgrading, the root device isn't detected by the 2.6.31 kernel, and I get dropped to busybox. The old 2.6.28 kernel does detect it, although it looks like the x server no longer works. The entries in grub are nearly identical for both kernels; the only difference is in the kernel path, not the uuid of the disk devices. How can I resolve the problem with the new kernel?

Edit: problem solved. The cause appears to be that my hard disks were incorrectly detected as being RAID devices by dmraid. Uninstalling the dmraid package solved everything, including the x server problem (deleting /etc/X11/xorg.conf may have helped too).

---

