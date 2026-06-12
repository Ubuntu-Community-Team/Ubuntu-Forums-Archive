---
title: "Cannot start Ubuntu, help me!"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by lnc on 2007-01-29
Hi everyone,
I have just installed Ubuntu 6-10 on my laptop, there are also WinXP on it.
It ran successful. But when i reboot my laptop, on the  GRUB screen, I see:
===================
Ubuntu, memtest86+
Windows Xp 
===================

Ubuntu, memtest86+ => Just test memory, Not start Ubuntu !!!
I cannot start Ubuntu. How can I start it? Help me.

---

### Post by yabbadabbadont on 2007-01-29
Try booting with the install cd again.  When it gets to its boot screen, there should be an option that says something like "boot installed system" or "first drive" or something like that.  See if it will boot the system.  If it does, then once you are in Ubuntu, open a terminal window and run, "sudo update-grub".  Look at the output closely to see if it lists any options other than the two you already have.  Post back here with the results (good or bad).

---

