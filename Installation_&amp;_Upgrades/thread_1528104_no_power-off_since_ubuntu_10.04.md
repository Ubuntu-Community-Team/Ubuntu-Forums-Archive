---
title: "no power-off since ubuntu 10.04"
date: 2010-07-10
forum: Installation &amp; Upgrades
---

### Post by alterpinguin on 2010-07-10
no power-off since ubuntu 10.04
- power-off did work on same hardware with older ubuntu 9.04
after different kernel-updates
for some time the kernel-boot-options:
acpi=oldboot
did work for me. But the latest two bigger updates broke this again
and i used a special menuentry 0 in grub to do a "halt" after a
reboot.
-
I looked for some more options and gave apm a try.
With:
apm=power-off nomodeset
my hardware can poweroff again.

If anyone suspects some backdraws using those boot-options, please drop a hint.

Changes were made in /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="apm=power-off nomodeset"
and i still did not try it with the options "quiet splash"
(but i use a grub-wallpaper while the grub-menu is displayed)
and activated with:
sudo update-grub

and maybe (because its only grml specific) i alway had to disable the noveau module in grml to run it from boot-CD
(grml is another linux-helper with debian?-based kernel 2.6.3x..)

---

