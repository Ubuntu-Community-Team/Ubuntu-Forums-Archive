---
title: "Screen Resolution wrecked on upgrade, none of the posted fixes work"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by sub_acoustic on 2008-11-07
I've been reading threads all day and following the advice of different people who have had the same issues as me, but none of those fixes have worked so now I'm at a loss of what to do.   

I have upgraded to Intrepid and my screen resolution is a fraction of what it should be, on startup it tells me that no device is enabled and I have to log in on a really low resolution.

I have tried, 
- manually rewriting xorg.conf
- reinstalling ati drivers and associated software (the ati drivers do not show up under Hardware Drivers even though they are definately there)
- using vesa drivers
- altering the screen resolution via the Screen and Graphics gui (gtkconfig), and the screen resolution tab (does not have my resolution there)
- going through the X setup but it only gives me the keyboard questions
- logging into the recovery session and trying xfix
- adding a display with xrandr but the documentation is kind of confusing for me 

So now I have the resolution of an old CGA monitor, but thankfully with more colours.  What can I try next?  I need to do work and need to be able to see what I'm doing first.  Any useful advice much appreciated!

---

### Post by sub_acoustic on 2008-11-08
ok, I think I know where the problem lies now
I get a **Segmentation fault** error whenever I run aticonfig --initial
when I try to initialise 

how can I fix this?

---

### Post by 10-10-20 on 2008-11-08
This suggests to me that the ATI driver set is not supported on 8.10.
Did you install the ATI restricted drivers from the Hardware Drivers utility, or hand install the drivers from the ATI website?

---

### Post by sub_acoustic on 2008-11-09
I can't see the ATI driver in the Hardware Drivers gui, I installed everything related to fglrx through synaptic.  I'll try replacing xorg.conf again with a backup - it seems aticonfig relies on xorg.conf even though the 8.1 way of doing things seems to have changed.

There's quite a few people who have succeeded with flgrx on 8.10 so at least it's theoretically possible to get my resolution back.  everything else seems to work fine.

---

### Post by sub_acoustic on 2008-12-23
After searching down many avenues I did what I should have tried first. A fresh install of Intrepid solved EVERYTHING.  Ubuntu how could I ever have doubted you!  My advice, do a fresh install don't upgrade.

---

