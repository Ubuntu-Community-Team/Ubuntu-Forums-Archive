---
title: "Need Strategy for Fixing 10.10 Upgrade that went bad!"
date: 2011-06-22
forum: Installation &amp; Upgrades
---

### Post by kendoori on 2011-06-22
Was running 10.10 64-bit on Thinkpad X201. I mistakenly clicked on upgrade this morning (really meant to just do a plain old update)... I tried to stop the process, but nothing that I did could get me out of the upgrade loop... so I eventually was forced to go ahead. Machine boots into 11.04; however, keyboard and mouse doesn't work. I have an external keyboard/mouse combo and that will intermittently work, but questionable. I was able to turnoff Unity; however, Classic doesn't seem to work with either external keyboard or laptop builtin.

My root and home are on separate partitions. I have a very fresh copy of home backed up on a separate drive. I don't have a recent backup of root...

If I could get Natty working with Classic (including minimize/maximize) I'd be OK...I'd be also OK with going back to 10.10 if I could do it without too much pain...

Meanwhile, I'm using another machine with Windows 7 so that I can at least do some work and come back to resurrecting my machine after I've had a bit of a timeout...

Help.................!!!!!

---

### Post by anoop999 on 2011-06-22
It might be easier to do a fresh installation rather than rescue a failed upgrade. If you do the new installation into your old root drive you can then change the mount location for /home so that it points to your existing home partition.

You would need to make a live USB or CD to install from.

---

### Post by kendoori on 2011-06-22
> **anoop999 said:**
> It might be easier to do a fresh installation rather than rescue a failed upgrade. If you do the new installation into your old root drive you can then change the mount location for /home so that it points to your existing home partition.

You would need to make a live USB or CD to install from.

Am I past the point of no return in regarding to 11.04, or is it possible to go back to 10.10 using this method?

---

