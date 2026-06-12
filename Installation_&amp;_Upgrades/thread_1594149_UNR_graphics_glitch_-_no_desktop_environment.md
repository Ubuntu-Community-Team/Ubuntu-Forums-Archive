---
title: "UNR graphics glitch - no desktop environment"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by Mard1kas on 2010-10-12
Hi!

I upgraded the UNR from 10.04 (which worked ok) to 10.10. Now, if I log in with the UNR session I get a weird graphics glitch (see attached screenshots). 
The panels are transparent and all the icons are invisible, though drop-menus seem to work (see: Unity02.jpg). 
Also, the side panel is transparent and does not display any icons (see: Unity01.jpg)

My system: MSI s420 laptop
video: radeon xpress 200M
cpu: dualcore intel of some sort
ram: 2 GB

What should I do to resolve the problem?

---

### Post by Mard1kas on 2010-10-26
In mean time I have tried to remove and reinstall Unity - no luck there. I'm suspecting the culprit is my video card... is there any other xpress 200 owners have faced the problem?

Though, I have not yet found similar issue.

---

### Post by clubbavich on 2010-10-29
I had a similar problem, but mine may have been more complicated.

I have an HP Touchsmart TM2T, with hybrid graphics.

What this means is that I have a low power Intel GPU, and a more moderate ATI GPU, and in theory, should be able to switch between them.

To get anything to work at all, I basically had to tell X to ignore the ATI GPU completely. 

Once I did that, I got the screen that you posted.

Then I had to uninstall the fglrx driver. Once I did that, everything worked fine. Well sorta... Unity keeps locking up, so I'm trying to figure that one out now...

---

