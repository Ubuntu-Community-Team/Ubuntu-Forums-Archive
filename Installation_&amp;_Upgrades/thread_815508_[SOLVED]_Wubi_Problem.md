---
title: "[SOLVED] Wubi Problem?"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by supercabbageuk on 2008-06-01
I've recently decided to give Ubuntu a go but I'm having problems installing.  I installed it last night using Wubi and all went well, however I tried to install my nVidia card and messed up so bad I decided to uninstall and try again.  I uninstalled Ubuntu through Windows and deleted the directory within Windows.

I went to install again a few minutes ago.  Wubi ran fine and my computer booted into Ubuntu to finish the install.  However when it tried to load Ubuntu again I received the following error.

```
Booting 'Ubuntu 8.04, kernel 2.6.24-16-generic'

Filesystem type is NTFS, partition type 0x7
Kernel /boot/vmlinux-2.6.24-16-generic root=VVID=3C10CFA110CF6106 loop=/ubuntu/disks/root.disk ro quiet splash

Error 15: File not found

Press any key to continue...
```

Any help on fixing this would be very much appreciated.

---

### Post by supercabbageuk on 2008-06-01
I managed to sort it, somehow one of the boot files was pointing to the wrong HD.

---

