---
title: "Gutsy Upgrade Nightmare: Screen Gone Haywire + Can't Fix Xorg! (ie Can't Use System!)"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by OzzyFrank on 2007-10-19
Hiya. Hate to say this, but thank god I have Windows! And really do hate to say this (seriously), but I should have known better to run an upgrade on Ubuntu, since I have seen so many tales of woe in the past. But upgrade I did, and the result is the screen goes haywire as soon as the login screen appears, and continues to do so when at the desktop. I can't see a thing as the display is rapidly moving diagonally, and have tried copying my failsafe xorg.conf over the one I assumed was messed with beyond hope, but while this has fixed issues with me trying to get fglrx drivers happening for my ATI 9200 card in the past, it has done nothing in this case.

I even decided to **dpkg-reconfigure xserver.xorg** but this did not fix things (mind you I just allowed some suggested defaults and specified settings i had before... maybe the monitor refresh of 65-90 is part of the problem??).

Anyway, I can get to a command prompt via booting into recovery mode, but this is the extent of how much I can use Ubuntu... so any suggestions will pretty much have to be command line, as I obviously can't see a thing once I get to the login and desktop. Please help, as not like I can use my perfectly-working Feisty system any more. Cheers.

---

### Post by OzzyFrank on 2007-10-20
If someone knows how to reset xserver to a basic/generic/default/failsafe setting, ie WORKING even with limited resolutions, please let me know... PLEASE?? I've always been able to get past display issues by replacing xorg.conf with my backup, or resetting xserver with the method outlined above, but now I am stuck with a desktop I can't see coz it is going out of control, no matter what I try. Usually I could also get into KDE or other desktop environments, but the login has gone spastic too. Interestingly, the mouse cursor is not affected. Any ideas appreciated, as I can't use Ubuntu, so am stuck in Windows for now. While I know stuff happens, I have to say I'm pretty disappointed with this situation.

---

### Post by bsh on 2007-10-20
boot to a command line
tpye:

sudo dpkg-reconfigure xserver-xorg

follow the steps, and set the graphics card to vesa or something basic. after done, save settings and startx

---

### Post by OzzyFrank on 2007-10-21
Hi, and thanks. Yes, my next step was to keep trying **dpkg-reconfigure**, and just go through the listed drivers till I found one that worked. I knew **vga** would be limited, and yeah upon boot it complains it can't give the 24-bit colour I asked for. Didn't think **vesa** would be any better, as for some reason thought that was even older. Trying to see if** s3** would work just ended in a black screen, no login, but while **vesa** is limited, at least it "works" and will do for now.

The limitation is that I can't get all the screen resolutions I specify. Please note that this does not mean I don't know how to specify more, it's that only 4 out of those I have listed in xorg.conf (either manually or by reconfiguring xserver) actually appear in the Screen Resolution applet. Not worried the max is 1280x1024... I was using 1280x960 anyway... but admit I am perplexed as to why my icons look smaller, and why there is a visible difference between desktop sizes. By this I mean that only one of the dimensions is slightly larger, ie the height, yet my icons are visibly smaller, and there is "blank" (ie desktop with no icons) to the right and at the bottom... like if I had resized to 1600x1200. If it wasn't for programs looking pretty much the same, I would have assumed (looking at the desktop) that I was indeed in 1600x1200.

Hopefully the Ubuntu team will soon fix their generic **ati** driver, so I can get my resolutions back. Still think that is majorly weird, since in the past any time I have specified resolutions, they appear in the list of those to choose from. I assume this is a limitation with **vesa** driver?

---

