---
title: "Cannot boot kernel 3.13.0-51 after dist-upgrade"
date: 2015-05-02
forum: Installation &amp; Upgrades
---

### Post by sblack55 on 2015-05-02
My system is Kodibuntu (Lubuntu with Kodi pre-installed) and it was at kernel version 3.13.0-49.  A dist-upgrade has installed kernel version 3.13.0-51 and seems to have worked normally, including updates to grub that should make -51 the default boot kernel.  However, it just keeps booting -49.  I have tried numerous edits to /etc/default/grub, followed by sudo update-grub.  /boot/grub/grub.cfg is modified, with -51 as the default menu item, but nothing changes in behavior, including the fact that the grub menu never appears.  I'm guessing Kodibuntu has mods that are getting in my way, but I have no idea what they are or how to defeat them.

Help!

(Linux noob, but not a complete idiot.)

---

