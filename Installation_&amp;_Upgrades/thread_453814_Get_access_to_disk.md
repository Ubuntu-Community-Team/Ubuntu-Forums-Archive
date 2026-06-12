---
title: "Get access to disk"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by jhenrik on 2007-05-24
Installed Ubuntu 6.10, updated it and upgraded to 7.04.  Ubuntu recognizes three disks in device manager, but one is not shown in the browser.   How do I make this disk available?

Would appreciate help.

Thanks

---

### Post by Big Ed on 2007-05-25
> **jhenrik said:**
> Installed Ubuntu 6.10, updated it and upgraded to 7.04.  Ubuntu recognizes three disks in device manager, but one is not shown in the browser.   How do I make this disk available?

Would appreciate help.

Thanks

Is it mounted?  In a terminal window, type "mount" to find out.  If it is, you can find it in the filesystem with Nautilus.  If not, then use the mount command to mount it somewhere.  "sudo mount device mountpoint"

Use "sudo fdisk -l" to find the device.

Ed

---

