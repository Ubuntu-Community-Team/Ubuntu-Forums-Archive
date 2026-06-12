---
title: "Help installing for the first time"
date: 2011-06-09
forum: Installation &amp; Upgrades
---

### Post by OverUnderOnward on 2011-06-09
So I've got a PC here that's several years out of date, is absolutely laden with useless stuff, and runs really sluggishly, do I decided to install Ubuntu and then format the Windows part of the hard drive.

Specs:
OS: Windows XP Professional
BIOS: Award Modular Bios v6.0
Processor: INtel Pentium 4, 1.70 ghz
RAM: 1024 MB
DirectX 9.0
Radeon 9500 Pro/9700 family Video Card
SoundMAX Digital Audio Sound card

Any other specs needed will be edited into the OP.

So I go for Ubuntu 11.04, 64 bit.  I try to install it and it goes to Busy Box, telling me that it can't find a medium containing a live file system.  A little bit of googling tells me to try the 32 bit version instead.  So Another download and burn later I give installing the 32 bit version a shot.  It goes straight to the purple loading screen with the Ubuntu logo in the middle and five color changing dots...  And stays there.  I left it for ten minutes and walked away, no progress.  So I decided maybe I'd just go the Long Term Support Route and burned a disk of ten.  Computer doesn't see the disk as a viable option - boots straight to Windows.

....Help?

---

### Post by Catharsis on 2011-06-09
Stick with the 32-bit 11.04 disk. Try these:

1) Check your CD for errors. When booting the LiveCD, you should see a purple screen with a keyboard and stickfigure at the bottom. Press any key here. It should bring you to a menu. You should see the "Check disc for errors" option; select it and see if there are any errors on the disk.

2) If the disk checks out, then get to the menu again by pressing any key during the keyboard/stickfigure page. Then press F6 and select "nomodeset" from the popup menu. You might have to press Enter again after selecting "nomodeset".

If that doesn't work there are other things you can try.


As a sidenote, I did the same thing you did with my Latitude D505 (Pentium M 1.4GHz, 512MB RAM). XP was so slow it was unusable, so I installed Ubuntu and it brought it back to life. I've since moved on to Lubuntu (a different member of the Ubuntu family) since Ubuntu was starting to drag a little recently, and it's running like lightning still. In short, Linux should treat your old PC very well :)

---

