---
title: "turn on acpi?"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by not_yet on 2008-07-01
I was unable to install ubuntu on a sony laptop until I set acpi=off

at the initial setup screen

how do I now turn it back on?

thanks

---

### Post by mikewhatever on 2008-07-01
Check your grub menu with <cat /boot/grub/menu.lst>. The particular line to look for should be similar to this [COLOR="DarkRed"]/boot/vmlinuz-2.6.22-15-generic root=UUID=a966c0-8100656fe2b81 ro quiet splash[/COLOR], with your version of the kernel and uuid. Make sure it does not have acpi=off attached. If it does, delete that part leaving the rest of it.
To edit the menu use <gksudo gedit /boot/grub/menu.lst>

---

