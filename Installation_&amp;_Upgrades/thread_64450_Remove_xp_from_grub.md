---
title: "Remove xp from grub"
date: 2005-09-11
forum: Installation &amp; Upgrades
---

### Post by chris86wm on 2005-09-11
how guys. i had windows xp and ubuntu installed on the same drive. i have since removed xp and resized ubuntu. however, windows xp still shows up on the grub menu. is there a way that i could remove it.

---

### Post by codejunkie on 2005-09-11
[QUOTE=chris86wm]how guys. i had windows xp and ubuntu installed on the same drive. i have since removed xp and resized ubuntu. however, windows xp still shows up on the grub menu. is there a way that i could remove it.[/QUOTE]
"sudo gedit /boot/grub/menu.lst" and remove the part about windows xp but make sure you back that file up first and have either the live-cd or install cd handy so you can restore your old menu.lst file incase your changes leave the system unbootable
hope this helps.

---

