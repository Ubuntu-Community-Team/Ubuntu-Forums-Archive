---
title: "Help! Tried Live CD, now WIndows won't boot"
date: 2006-05-16
forum: Installation &amp; Upgrades
---

### Post by simon tahiti on 2006-05-16
Hi, I'm a definite hobbyist rather than a power user. I have an old P3-600Mhz machine upon which I installed ubuntu a few months ago, and have been learning about it very slowly.

Today I tried putting the ubuntu live CD into my other Windows machine (the main one with all my apps and data on it) to see how it would run on a fast machine. It was very good...except that now Windows won't boot at all on that box.

I get a black screen and an apology about Windows not starting normally. I am presented with various safe mode options, as well as "last known good configuration" and "start Windows normally".

None of these options do me any good, because whichever I choose, the "WIndows is starting" message shows for about 30 seconds (with status bar thingy scrolling as usual) but then the machine reboots and goes back to the error message. It's the same whatever option I choose at the error message. It's also the same if I try to boot from my XP CD.

Anyone know what's going on? What could the Live CD have altered on my machine to make Windows so unhappy? I DESPERATELY need access to Windows on that machine so would certainly appreciate any help.

---

### Post by syg00 on 2006-05-16
Mmmm - sounds a bit naughty. You're sure it was a liveCD,and not an install CD ???. Must admit I've never seen a Ubuntu liveCD.

Exact error messages would be nice.
Get a decent liveDC (Knoppix is my choice), and post the output from "fdisk -l" (that's ell, as in list).

---

### Post by derjames on 2006-05-16
That is very strange... The LiveCD does not install anything i.e. does not "touch" your hard drive in any way... are you sure it was the LiveCD???

---

### Post by simon tahiti on 2006-05-16
Well, the error message is pretty long. Here's what it looks like:

[IMG]http://www.simontahiti.com/modules/xcgal/albums/userpics/error_msg.jpg[/IMG]

Here's the last thing I see if I try to boot into safe mode:

[IMG]http://www.simontahiti.com/modules/xcgal/albums/userpics/safe_mode_stops.jpg[/IMG]

Yes, it's definitely a Ubuntu live CD. Ubuntu 5.10 "Breezy Badger" to be precise. I've used the same CD to demonstrate Ubuntu on various other Windows machines without any trouble.

It was the "harmless, doesn't install anything" nature of the live CD that made me bold enough to stick it into my main PC without any concerns.

---

