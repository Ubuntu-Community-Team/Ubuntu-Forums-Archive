---
title: "[SOLVED] Hardy install PS3 problems..."
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by James- on 2008-04-25
I downloaded the latest ISO for the PS3 and power PC. I install the kboot(really changed since the last one <3 tux) I type in 'install video=ps3fb:mode:133'  I see the ubuntu logo with the usual loading bar and then it freezes with a little underscore(I waited over 10 minutes) and it was still stuck with the underscore

---

### Post by fwilliams on 2008-05-27
I have tried multiple times and have the same problem.  I have reformatted the p3s disk before trying the install and have tried installing with:
install video=ps3fb:mode:5
install video=ps3fb:mode:3
install

Every time it seems to start the install process and then just hangs with the cursor in the upper left corner.

---

### Post by sohailjuna on 2008-07-09
Hey guys,

I had the same problem.

I am not sure what kind of TVs you guys are using, but I will assume they are HD Ready ones.

Installing

When I first installed 7.10 on my PS3 with the default video mode enabled all the windows were way too big so that you couldnt use them.

So the answer is to type the folowing command at the kboot when you want to install it:

install video=ps3fb:mode:[X]

[X] comes from using one of the options below  

YUV 60Hz  1:480i  2:480p  3:720p  4:1080i  5:1080p
 YUV 50Hz  6:576i  7:576p  8:720p  9:1080i 10:1080p
 RGB 60Hz 33:480i 34:480p 35:720p 36:1080i 37:1080p
 RGB 50Hz 38:576i 39:576p 40:720p 41:1080i 42:1080p
 VESA     11:WXGA 12:SXGA 13:WUXGA

HOWEVER - I found that the maximum res you can go up to in the install is 720p (3)

ALSO - I found that the only way it worked for me was to go back to the PS3 OS (XMB) and start the whole proceedure again

1 - Format HD
2 - Install other OS

etc

Hope this helps

Sohail

---

