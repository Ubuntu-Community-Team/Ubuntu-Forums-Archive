---
title: "Between a rock and an OS"
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mickeymartin on 2008-10-21
Complete noob here. 

I just put together a new system (AMD X2 5200+, Gigabyte MB MA78GM-S2H, AMD 780 chipset). Could not get HH to boot completely. Did a search and found someone with similar hardware and similar problem. One of the replies mentioned that the issue had been fixed in II so I downloaded 8.10 beta which successfully loaded. Joy. Much to my surprise there appears to be no desktop loaded (?!). When the machine boots up all I am left with is wallpaper. I can right click and get to a menu, but it has limited choices. I decided to try again and load HH 8.04 with the suggested boot change, but it still does not load.

Help! What happen to gnome? Is it missing since 8.10 is beta?

What should I try now?

Thanks for the help. I hope to be able to pay it forward once I get up to speed in Ubuntu.

Mickey

---

### Post by wolfen69 on 2008-10-21
to try and narrow down the problem, you should try to boot another linux live cd of another distro. (or 2) that way, if nothing boots properly, chances are you have a hardware problem.

---

### Post by eternalnewbee on 2008-10-21
If 8.10 loads, but 8.04 doesn't, it could be that 8.04 wasn't burnt correctly. Try burning it at speed 4, and see if the problem still persists.
Good luck.

---

### Post by cariboo on 2008-10-21
For quicker and better help with your question you should ask it here:

[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

Jim

---

### Post by evilkastel on 2008-10-21
You might consider aswell to check the integrity of the LiveCD with the option it gives at the "try Ubuntu-Install Ubuntu...etc." screen.

---

### Post by mickeymartin on 2008-10-22
Solved!

Thanks everyone.

It turned out to be a poor burn on the CD.

I had checked MD5 but did not run the integrity check. The integrity check found 1 bad file. After reburning the CD at 4x and including the pci=nomsi command everything worked perfectly.

Mickey

---

