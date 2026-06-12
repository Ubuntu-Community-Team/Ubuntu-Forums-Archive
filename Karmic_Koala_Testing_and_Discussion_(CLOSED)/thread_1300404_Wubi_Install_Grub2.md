---
title: "Wubi Install Grub2"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by carbm1 on 2009-10-24
If you install with Wubi and update for some reason the MBR on the disk is over written leaving Ubuntu the only bootable option in Grub2.  When you select the Windows menu item it pops up an error about...

error: unknown command 'drivemap'.

Anybody else replicate this?

What I have done as a temp fix is download ms-sys and 'sudo ms-sys -w /dev/sda' and suddenly I get my normal boot.ini options.

Is this just a bug... Please tell me it will be fixed before the official release.

Thanks,

Craig

---

