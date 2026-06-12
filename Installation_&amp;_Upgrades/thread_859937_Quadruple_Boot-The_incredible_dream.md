---
title: "Quadruple Boot-The incredible dream?"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by spiritfox on 2008-07-15
Hey all.  I'm building a computer sometime in the next week.  I love linux, but I need XP for games and work, and OSX for school.  I also wanted to try out FreeBSD.  The build will have two 500GB hdds.  I was planning on hooking up one hard drive at a time, on the first one I would install XP, then Ubuntu and set each partition to ~250GBs.  The other disc would have OSX86, and then an install of FreeBSD, also on 250GBs each.  I was just wondering if anyone had any experience with anything like this, and if so do you know if GRUB can handle it?  I would be willing to try Lilo if that would work better, or really any other bootloader, just so long as it works.

---

### Post by houbysoft.xf.cz on 2008-07-15
I think that GRUB should handle all without problems, my system is even "bigger" than Quadruple boot, it has Windows 98 (dunno why I still have it), Windows 2k, Windows XP, Xubuntu 8.04, OpenBSD, Gentoo, and my own OS :D. So quad-boot should work without problems, only I don't have any experience with OSX86, can't say if it will or won't work.

---

### Post by bob_hilton on 2008-07-22
I want to do this aswell but to test a few other linux distros on the same disk.

I've got XP on one partition and ubuntu in another and have two more primary partitions on my disk. When i'm tring to install arch, it wants to use the remaining partitions as / and /home, therefore leaving me no more space. 

Has anyone else had experience of installing 4+ that can help me with partitioning?

---

### Post by TrueLugia121 on 2009-01-07
yeah i was actually thinking about doing the same thing except i don't have no knowledge of OSX86. what i have on my father's laptop so far is 57GB for Windows XP SP2, 68GB for Ubuntu 8.10 Intrepid Ibex and roughly about 116GB for Linux Mint 6 Felicia.


issit possible to cut Felicia's partition in half without resizing XP's?

---

### Post by CWindowsRun on 2009-02-16
I got my laptop running Ubuntu XP Vista and Backtrack3final(soon to be 4 
!!!!) and it works perfectly, bit of trouble with Vista and xp not liking the others boot settings(ironic no?), but once that was out of the way Grub did the trick nicely.

Dont see why you couldn't get mac OS to work also, hell i might go for five just to see!

my only advice is install ubuntu last because more than likely if your boot settings are correct grub will recognize it and youll be ready to...

...have fun doing gratuitous boots into several operating systems?

---

