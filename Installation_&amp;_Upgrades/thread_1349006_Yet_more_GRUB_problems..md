---
title: "Yet more GRUB problems."
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by justyellowboy on 2009-12-07
Kinda hard to explain in a tiny little title, my apologies.
 
 
 
So, I recently slapped on Ubuntu 9.10 with Dual Boot Windows 7, sucessfully, managed to get internet, sound, and video successfully working on my Dell Inspiron 15 notebook. A couple program installations later and it was a party!
 
Well, in came Update Manager while I was doing cool stuff in LMMS, and was all, "DUDE UPDATE LOTS OF STUFF HERE!" and I was all, "Well, they must be stable if they're releasing them like that!" And downloaded the loads of updates available.
 
It told me to reboot, which had never happened before, but I went with it anyway. Back to the Dual Boot screen, selected Ubuntu, and I expected the GRUB menu to change in some manner, and boy did it ever.
 
GRUB isn't loading Ubuntu, now. Instead, it has a command prompt that I *dearly* hope I won't have to mess with every time I get on Ubuntu. Now, it gives (unexplained) commands that I can enter (and I'll be looking at those, later).
 
 
 
Basically, I've had it. I'm rolling up my sleeves and desiring Dual-Boot, partition-style (I don't know what I'm talking about D:), probably 'cuz GRUB is thinking in Partitions, (or maybe commmand prompts.)
 
What I want to do is find and save a folder filled with my files located in my Home folder (should be easy with the LiveCD and its testing features), uninstall Ubuntu and re-install it on a partition (after using the standard Ubuntu, I'd like to see if anyone can recommend me the variation of Ubuntu that can run the most programs (Uni-Verse, LMMS, Education packages, KDE stuff, etc.)
 
Feel free to point and laugh at the 90% of my senseless jargon, and also the fact that I should have looked into the updates in the first place.

---

### Post by outerspacerace on 2009-12-07
[http://ubuntuforums.org/showthread.php?p=8459578#post8459578](http://ubuntuforums.org/showthread.php?p=8459578#post8459578)

Updates just killed my dual boot too. I have liked each version of ubuntu successively since I came on board with Hardy but Karmic isn't holding up too well for me thus far.

---

### Post by justyellowboy on 2009-12-07
You can't boot into 7? Weird! "No signature of what, exactly?" is my question.
 
It's telling me that there is no kernel loaded. So, I'll try loading the kernel and booting.

---

### Post by outerspacerace on 2009-12-07
[http://ubuntuforums.org/showthread.php?p=8460333#post8460333](http://ubuntuforums.org/showthread.php?p=8460333#post8460333)

For reference.

---

### Post by darkod on 2009-12-08
For reference, this sounds much like the problem with wubi after doing kernel updates. But if you have wubi you do NOT have dual boot (some here have opposite opinion).
Dual boot is usually general term for having windows and linux on separate partitions. Wubi install ubuntu INSIDE windows and that's part of the problems with it. You're trying to make linux work inside windows and all sort of unforseen issues can come up.
You are right, if updates are issued they must be stable. Those updated don't brake down a side-by-side dual boot install (I have done them on both my desktop and netbook) but there are issues with wubi.
In case you have wubi let me know and I'll send you a link how to fix this (temporarily).

---

### Post by outerspacerace on 2009-12-09
Oh no, thanks anyway but I dual boot. 

Sorry for not mentioning it. I just posted in your thread in as the problem seemed update related.

---

