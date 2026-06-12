---
title: "Ubuntu/Win 7 compatibility."
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by Tuxaby on 2009-11-26
Are there any problems running Ubuntu  and Windows 7 side by side?  Going to buy a HP Pavilion dv7-3067cl from Sams Club. First thing will be to repartition and install Ubuntu 9.1.

---

### Post by phillw on 2009-11-26
Hi,

side by Side is kewl to go. Wubi, however, has reported problems within win7.

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

Has a tutorial on it, with screen-shots.

Regards,

P{hill.

---

### Post by darkod on 2009-11-26
I am running dual boot of win7 and desktop 9.10 on both my desktop and netbook. No problems at all. But I had the opportunity to do clean installs on both machines and that helps a lot I guess.
After shrinking the win7 partition, if that's your plan, I would boot win7 few times and even work on it few days to see if it's "happy" after the partition shrinking. And definitely let it do any disk checks that it asks for on the first boot after the shrinking. I think it's better that way. And because of that I never recommend to do the shrinking and install of ubuntu in one go, with the ubuntu installer.
Either shrink the partition with win7 disk management (not really first choice), or boot with ubuntu cd, select Try Ubuntu option and use Gparted to shrink the partition. Just that, no need to create ubuntu partition at that moment, you would have to redo mount points in the ubuntu installer later anyway. Gparted seems to handle shrinking partitions much better than windows disk management.

If it's up to me, I would split the process. First shrink and use win7 few days to see if it's OK, then install ubuntu.

---

### Post by Tuxaby on 2009-11-26
Great, it's a go.  I always partition from CD.  I do it with Linux always.  Great replies, as always.   I like howtos, there is always something new to learn from them.  I hadn't thought about letting Win 7 settle a few days after partitioning.   Been partitioning  WinXP and then installing Ubuntu without any problems. Makes  sense though and could shortstop problems with the new OS. Don't know if it will make a difference, but I will wipe the drive first, partition it, reinstall Win 7 without all the unwanted bloat-ware, then install Ubuntu.  I'm a very patient person, so will wait a few days in between installations just to be safe.  Can't hurt.   Thanks phillw and darkod , appreciate the always valuable input.  Lee

---

### Post by darkod on 2009-11-26
No problem. If you are wiping it and installing win7 only on part of the drive, it's the ideal situation. I did the same. And this was my first touch with ubuntu. No problems of any kind, grub2 picked up win7 and all worked "out of the box".
The shrinking can be problematic, corrupting windows. That's why I prefer two step method because you need to know if windows was OK after the shrinking, and not blame ubuntu for it. :) If you do it in single step you can never be sure.

---

### Post by phillw on 2009-11-26
+1 darkod

Yeah, Win *can* get the right hump after a resize. I think XP was the one that screamed like a kid having a hissy-fit. Vista was fairly quiet and just asked for a quick disk-check. But, deffo, letting Win get it's act together before proceeding is a good one. Makes Grub2's life a whole lot easier ;)

Regards,

Phill.

---

### Post by Tuxaby on 2009-11-26
Thanks for the help.  Next stop,  Sam's Club.

---

