---
title: "busybox after update"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by bdog676 on 2008-05-25
I installed updates today and after I rebooted, I get a message saying busybox v1.1.3 type help for commands. I have tried using the .bak on the initramfs but still not working.

---

### Post by dstew on 2008-05-25
Edit the kernel line to remove quiet splash (from the grub menu, press 'e' to edit). Then, see if you can tell what the exact error is before it gets to the Busybox prompt. You can use alt-<pg up> to scoll the display up if you don't see the error on the page.

---

