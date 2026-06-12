---
title: "Installation cd gives errors on one pc, none on another"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by spupy on 2008-04-15
I have here my 8.04 beta installation cd. On my computer (Toshiba Satellite A110) it boots OK, and I was able to install Ubuntu with no problems.
However, today I tried installing Ubuntu on a friends laptop (Averatec 3700) using the same cd. It boots and gives the menu with "Install ubuntu", "Try ubuntu" etc. But when anything is selected, it starts it for a while, then gives some prompt with "(initram)" at the start of the line. There are some commands available, and it says "Busybox version..." at the top. I've been using Linux for over an year, but never met something like this and I have no idea what would cause this error on my friends laptop, but not on my own. What should I do with this prompt? Should I do anything? Maybe try with 7.10?
Any help is appreciated.

---

### Post by gn2 on 2008-04-15
Try pressing F6 and type: acpi=off
Then press Enter

---

### Post by zero-g on 2008-04-15
Can also try the -noapic, my hp notebook will not boot without it and a different ver of ubuntu doesn't help either. think its a hp bios prob...

---

