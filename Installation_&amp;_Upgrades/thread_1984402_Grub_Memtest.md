---
title: "Grub Memtest"
date: 2012-05-21
forum: Installation &amp; Upgrades
---

### Post by bikertappy on 2012-05-21
OK, I now feel like a complete numpty but:

I've a new install of 12.04 LTS on a brand new PC and I can't get a grub menu up during boot. I've tried all the bios options that are flagged up, and tried holding "Shift" but it makes no difference.

I'm getting some random crashes and want to test the memory - is there another way to do this without grub at start up? In "System monitor" it's showing 3.7Gig on a 64bit machine, with 645-bit ubuntu, and 4Gig of RAM installed. Suspicious?

---

### Post by Doug S on 2012-05-21
I don't know if this will help but ...
I find the default time for the grub menu is just too short. Often, the display doesn't show, or just flashes quickly. So, I usually edit the /etc/default/grub file to increase the timeout. Change this line:```
GRUB_TIMEOUT=2
``` to say 10 to have plenty of time to see the menu. Note that you will have to run this after the edit:```
sudo update-grub
```

---

### Post by bikertappy on 2012-05-23
Spot on Doug - it wasn't the timeout that was wrong (set to 10 seconds) but it was set to hide and quiet so it simply didn't display anything! Now adjusted so I can actually see the GRUB menu, and I've been able to run memory tests. Many thanks :)

---

