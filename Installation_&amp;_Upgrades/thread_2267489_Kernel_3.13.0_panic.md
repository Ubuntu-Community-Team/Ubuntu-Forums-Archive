---
title: "Kernel 3.13.0 panic"
date: 2015-03-01
forum: Installation &amp; Upgrades
---

### Post by dtomas2 on 2015-03-01
Hello.
I'm running Ubuntu 14 LTS on vmware vritual machine.
I compiled a new version of kernel 3.13.0 with [FONT=courier new]make install[/FONT], [FONT=courier new]make modules_install[/FONT] and got the *bzImage* file.
I copied the file to /boot and run [FONT=courier new]sudo update-grub[/FONT].
Should I use the *bzImage* or *vmlinux.bin* file?

When I restart Grub2 shows the new compiled kernel but when I choose it I got a "[COLOR=#ff0000]kernel panic-not syncing: VFS: unable to mount root fs on unknown block(0,0)[/COLOR]" .
[ATTACH=CONFIG]260374[/ATTACH]

Anyone has any guess how to fix this?

Thank you.

---

