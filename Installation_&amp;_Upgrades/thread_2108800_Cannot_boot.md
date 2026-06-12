---
title: "Cannot boot"
date: 2013-01-25
forum: Installation &amp; Upgrades
---

### Post by frash23 on 2013-01-25
Hello! I am having a problem with my laptop.
I installed wubi, and marked it as default boot using boot properties in windows. Somehow, some of my keyboard buttons are disabled in boot ._. i plugged in an external keyboard, same issue.
Wich means, i cannot select windows when i start up. All buttons i have are F12 and space, actually. My wubi installation glitched up, and i get in to a grub minimal bash terminal when i startup. I am not able to get to the HDD any other ways (no reader) and i do not have any CD, and i am not able to burn one.
What do i do?

---

### Post by bcbc on 2013-01-26
If you have Windows 7 you can use a Windows repair cd to change the default using bcdedit

If it's XP you can edit the boot.ini (carefully) from Ubuntu.

---

