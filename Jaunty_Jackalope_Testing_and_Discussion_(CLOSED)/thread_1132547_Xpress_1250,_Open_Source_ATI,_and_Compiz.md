---
title: "Xpress 1250, Open Source ATI, and Compiz"
date: 2009-04-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by skyh on 2009-04-22
So, I've done a pretty good amount of searching, and I haven't found anything specific yet on the matter, so here it is.

I have an Acer Extensa 5420, 2 gigs of a RAM, with ATI Xpress 1250 video.

I installed Jaunty around Beta 3 and have been using it since, and since that time, the ati open source driver. Now, recently I tried installing the new fglrx driver, only to have it tell me it doesn't find a supported card, then to discover than ATI is dropping new support for this card. Well, great.

So if I'm to continue using the newer versions of Ubuntu and all the goodness that comes with Linux improvements, I have to use the open source driver. Knowing this, and knowing that things are still supposed to work with the open source driver, I enabled Compiz...

However, this turned out to be less than usable. Any sort of screen changes are unbearably slow, including everything from scrolling to dragging a window around. Not to mention when something is supposed to fade it, it wipes instead. Incredibly, incredibly slow.

glxgears gets me around 340 FPS, which is okay I guess considering I only got around 800 FPS with fglrx..

Also, I've tried reinstalling all the mesa stuff, have completely gotten rid of everything fglrx on my system (that I know of), and have tried using "AccelMethod" "XAA" all to no avail. Not to mention, the whole

Section "ServerLayout"
    Option   "AIGLX" "true"
EndSection

on the ATI Xpress page (yes, I do realize it says you shouldn't need to to that at 8.10 and above) breaks the xserver. Dunno if that even matters in any way, just thought I'd mention it.


So, thoughts anyone? Anything anybody has heard about this? I'd imagine if my issue isn't unique then there will be plenty of questions about this once 9.04 is released and people realise that they can't use FGLRX anymore on their Xpress chipsets...

---

### Post by danwood76 on 2009-04-22
There is a regression in the mesa dri for the r300 driver, which I assume yours uses.
See this thread: [http://ubuntuforums.org/showthread.php?t=1120175&page=3](http://ubuntuforums.org/showthread.php?t=1120175&page=3)

This may give you better performance.
I see no issues with the open source drivers and compiz, I get about the same fps as you do in glxgears on my x200m

---

### Post by skyh on 2009-04-22
Perhaps that's what is causing it.. I did try patching the r300_dri.c in the source of the most recent mesa and compiling.. to no avail unfortunately. Although, if I do run my processor at performance level (1.9 GHz), then I get around 800 FPS, so.. I guess that's what I'll be expecting.

However, there definitely is a problem with Compiz for me. Although glxgears looks fine running at 370 FPS or so, Compiz definitely isn't getting anywhere NEAR that. So unless Compiz has never run smooth in any way on the open source drivers for my card, there must be an issue there, and I'm not sure if it's another part of the regression in the r300 driver or what. Even running my processor at 1.9 GHz, Compiz still has unusably poor performance. For example, if I tried to drag a window around the screen quickly, you'd probably only see the window redrawn about a total of 5 times in a few seconds.

By your response, dan, I'm guessing that you don't have this issue with Compiz? (P.S., at this point, unless I find something otherwise, I'll probably just be doing a clean install of the release to make sure)

---

### Post by danwood76 on 2009-04-22
I dont have any issues with compiz, although I normally have desktop effects set to normal.
I just enabled the extra and the wobbly windows etc rendered fine.
I'm just re-compiling mesa to test the patch.

I tend to have them off to save battery.

---

### Post by neekz on 2009-04-22
I have the same gpu and cant get Compiz to be activated at all I hope someone has some workaround.

---

### Post by skyh on 2009-04-22
On another note, whenever I do enable it, the "Searching for drivers" box comes up... it does something for a small amount of time, but then Compiz enables fine.. it just doesn't run at a speed where it's even usable.

---

