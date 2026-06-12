---
title: "Grub broke after formatting"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by skizz on 2006-11-05
Hello there! I've had Windows XP and Dapper 6.06 on my computer, dual-booting using GRUB. Yesterday, I formatted my Ubuntu partition (needed more space). When I turned my computer on this morning, Grub was showing me an error, and I couldn't boot from my XP partition.

Thanks, 
A.

---

### Post by MWAAAHAAA on 2006-11-05
So are we supposed to guess what the error was, or are you going to show us?

---

### Post by skizz on 2006-11-05
Error 17, obviously. Grub couldn't load.

LATER EDIT: M'kay, problem solved using ```
fixmbr
``` in the Windows Recovery Console.

---

