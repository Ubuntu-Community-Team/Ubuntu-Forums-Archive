---
title: "linux mint get acpi=off set into boot config"
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by leo5111 on 2008-03-13
when i installed it i found out even when it was installed i have 2 hit f6 then at end of boot up line put acpi=off i found out 100% its the culprit i dont put it it freezes i put it it boots fine please someone tell me how to change the boot file or whatver to add that line please? i know wrong disgtro forum but no is answering over at linux mint forums :popcorn:

---

### Post by plucky on 2008-03-13
> how to change the boot file or whatever to add that line please?

Open a terminal,then to be safe  make a copy of menu.lst ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bck
```

To edit the file ```
gksudo gedit /boot/grub/menu.lst
``` add **acpi=off** to the kernel line and to the line > # defoptions=quiet splash acpi=off so that it is kept after kernel upgrades.

Good luck

---

