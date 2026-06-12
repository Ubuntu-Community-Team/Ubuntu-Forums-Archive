---
title: "problem booting ubuntu studio"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by ektober on 2008-02-01
I have trouble booting ubuntu studio. If I in the kernel line add "noapic acpi=off" ubuntu studio will load to approximately 40% but then stop and nothing happens. I tried removing "quite splash" and then the computer locked itself after a line ending with "[ipw2200]". The immediate lines above dealt with "[usbcore]".

What I need help with first of all is as basic as reading the log-files in rescue mode. Gedit won't work, it can not open in a display when I'm in a shell and I really don't have a clue what happens when I open with Vim I certainly don't see any text, also I'm unable to scroll up and down in the shell. How do I do such a thing.

---

### Post by ektober on 2008-02-03
It's working now that I've added "pnpacpi=off" inte the kernel line in bootup and in boot/grub/menu.lst .

Bu still I'm wondering about what is wrong and if/how I can solve it.

---

