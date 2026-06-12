---
title: "new installation works but freezes - advice to debug it?"
date: 2005-09-24
forum: Installation &amp; Upgrades
---

### Post by michaelbg on 2005-09-24
Hi,

This is my first installation of ubuntu.  hoary 5.04.

I enjoy the package management (compared to say Mandrake.) 

However, there are two problems.

1)  the system freezes regularly, and has to be hardware reset.
2)  the gui performance seems poor, ie. sluggish.   I have a radeon 7000 (I know it's an old card, still, should I seeing windows tracks as I move them around?  I didn't see tracks in mandrake. ) It's using the ati driver for xorg.  I installed everything in ext3, would that be a factor in slowing it down?

Of the two, the most annoying is the crashing. 
Typically, I will be running a few apps and click on something, and suddenly nothing moves. The screen is completely frozen.  Here are my meager findings.

1) I have successfully left the system on overnight and it did not crash.  So the crash seems to be linked to my actions. ie. passively it does not seem to fail.

2) I have successfully run multiple apps simultaneously. Watching a small movie, while downloading ubuntu updates and browsing the web...for over an hour without any problem.

3) none of the logs in /var/log appear to show any problem.

So are there logs in other places I should be looking at?  or tests I could run?

thanks for any help you can give.  I am willing to give this  a few more hours of work, otherwise I'll have to install another distribution. The random crashing drives me up the wall.

sincerely
Michael

---

### Post by michaelbg on 2005-09-24
So, I have two new pieces of information.  I left the computer on with gtk-gnutella, figured that would keep some activity up on the computer while I was gone. I came back and the computer had crashed.  So it's perhaps not an interface issue.

Also, earlire I had installed and tested telnetd.  Post-freeze, I can't login. So the computer is quite frozen. keyboard (ctrl-alt-delete and ctrl-alt-backspace do nothing.)  oddly, in windows, when the system freezes if you hold down keys it eventually beeps at you, but not here, but perhaps that's irrelevant. Does anyone know where would a kernel panic would be recorded, if there was one?

thanks,
Michael

---

### Post by mlomker on 2005-09-24
> 
2)  the gui performance seems poor, ie. sluggish.   I have a radeon 7000 (I know it's an old card, still, should I seeing windows tracks as I move them around?  I didn't see tracks in mandrake. ) It's using the ati driver for xorg.  I installed everything in ext3, would that be a factor in slowing it down?


Probably want to switch to the 'radeon' driver.  Look here [http://dri.freedesktop.org/wiki/FrontPage](http://dri.freedesktop.org/wiki/FrontPage) for more info.

> 
thanks for any help you can give.  I am willing to give this  a few more hours of work, otherwise I'll have to install another distribution. The random crashing drives me up the wall.


You mention in a later post crashes in Windows...you have a hardware problem, not a Ubuntu issue based on that information.  You could try selecting 'memtest' from the grub menu to test your memory.  Other than that the best approach is to remove every piece of removable hardware and see if it still crashes...then slowly add it back.

---

### Post by michaelbg on 2005-09-24
In my second post, I mentioned previous windows crashes but I was speaking historically.  My current hardware does not crash in windows.

I will try the radeon driver, although I had actually read in the forums somewhere  that the ati driver was quicker than the radeon driver. It's worth a try. 

I'm not too sure how to change that but I will look it up.  

Michael

---

### Post by mlomker on 2005-09-24
> I'm not too sure how to change that but I will look it up.  


Try them both!  It's easy.  **sudo dpkg-reconfigure xserver-xorg**.  You can then run **glxgears** to check the performance.

I'm not sure if either of the Hoary drivers have 3D support.  The drivers that I linked to do.

---

