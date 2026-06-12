---
title: "Edit GRUB boot menu to include Windows"
date: 2016-03-22
forum: Installation &amp; Upgrades
---

### Post by jmelton on 2016-03-22
After fixing GRUB following a stalled Linux update that left me without a GRUB menu and only allowed me to boot into Windows, now Windows doesn't show up on the GRUB menu and I can boot into Linux but not Windows. How do I fix this?

---

### Post by Bashing-om on 2016-03-22
jmelton; Hello;

What results with terminal commands:
```

sudo apt update
sudo apt upgrade
sudo update-grub

```
Where it is expected that grub will chainload Windows onto it's boot menu .

[INDENT][INDENT][INDENT]Maybe Yes
[/INDENT][/INDENT][/INDENT]

---

### Post by Edison_James on 2016-03-23
The above commands, worked for me when I experimented with them.:)

---

