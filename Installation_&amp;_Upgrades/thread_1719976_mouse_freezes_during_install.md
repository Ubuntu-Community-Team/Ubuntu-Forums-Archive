---
title: "mouse freezes during install"
date: 2011-04-02
forum: Installation &amp; Upgrades
---

### Post by pottzie on 2011-04-02
This is going to get ugly. I'm chasing one of those problems that could be Ubuntu, could be hardware, or could be psychic phenomena. I started this mess off by trying to go from Ubuntu 10.10 to the new 11.4 beta (now alpha?) by doing update-manger -d.  It got stuck several times, and locked my  computer up. By locked up I mean that the upgrade stopped loading, and the mouse became unresponsive, just stuck in one place on the screen.  It said I could only do a partial upgrade, and I kept at it, but at some point I rebooted into a gnome splash screen that showed the few icons as white files, no top or bottom panels, and a dead mouse/cursor.

 I had ndiswrapper and VirtualBox installed, and thought maybe that was what made everything go south, so I decided to just reinstall 10.10 and start from scratch. Even that was a little buggy, but the real problems came when I tried to update. The GUI package update died, or had something happen while I was away from the computer (something like 256 updates-hey.)   The log-in screen didn't show the updates and I rebooted to redo them. This time I went with "sudo apt-get update" and sudo apt-get upgrade."  No problem until the system froze again, this time with the terminal saying "copying image linux kernel 2.6.33(something) to initrd" or words to that effect.  Not exactly what you want to happen. When I rebooted, Ubuntu was there but the mouse was not working, and it's been that way ever since then.
 I have two computers on this hook up, and they share a cable so they both use the same mouse, keyboard and monitor. When I switched to the other computer to sanity check things, my mouse didn't work on that one either, so I decided that the mouse was the culprit, and broke down and sprung for a new mouse. But now that I've installed it, the mouse works great with the other computer, and not at all on the one with Ubuntu.

 I'm going to reinstall Ubuntu and see what happens, but I figured I'd throw this out and see if anyone had any advice the doesn't include references to gasoline and matches.  This all happened using a several years old generic Compaq PC computer with not much of anything as far as bells or whistles.

---

### Post by Hedgehog1 on 2011-04-02
Mouse stuck?  Hmmm...  **It COULD be an 'OUT OF CHEESE ERROR*'. ** :D

If you are still having issues by the time you read this, would you please boot off the LiveCD/LiveUSB, select TRY, and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.


***The Hedge***

:KS

****** This is a reference to a disk-world book, by the way...*

---

