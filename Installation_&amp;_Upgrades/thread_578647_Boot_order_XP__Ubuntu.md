---
title: "Boot order XP / Ubuntu"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by ray-in-ojai on 2007-10-17
[SIZE="4"]Does anyone have a detailed list on how-to boot XP first then Ubuntu.

Ray[/SIZE]

---

### Post by vishzilla on 2007-10-17
> sudo gedit /boot/grub/menu.lst
around line 14
> default		0
change 0 to 4

save the file and exit...you should be fine

PS: in the grub menu check out what entry is XP, starting with 0 from the top, that entry should be put in the line "default..."

---

### Post by ray-in-ojai on 2007-10-17
[SIZE="6"][COLOR="SeaGreen"]Perfect !![/COLOR][/SIZE]

---

### Post by Zugzwang on 2007-10-18
By the way, how to make sure that after every Ubuntu upgrade, it **remains** default to boot Windows? :)

---

### Post by Eddie Wilson on 2007-10-18
Good Day,
Upgrading should have no effect on boot order. It never has in the past with me.
Eddie

---

### Post by jdr00ejr on 2007-10-18
When I upgrade, if the kernel changes, it adds a kernel to the grub list, pushing XP down on the list.  More times than I can count, I've run the Update (which loaded a newer kernel), and then when my computer reboots, if I'm not paying attention, I go into a perpetual MemTest cause everything was bumped down the list by 2.

Now I can easily fix it but going in and adjusting my default in the grub settings....just frustrating.  So I can sympathize with the poster who asked.

---

### Post by John Bennett on 2007-10-18
> **jdr00ejr said:**
> When I upgrade, if the kernel changes, it adds a kernel to the grub list, pushing XP down on the list.

There is a section of the menu.lst file that grub never modifies.  Put your XP boot instructions in that section.

---

