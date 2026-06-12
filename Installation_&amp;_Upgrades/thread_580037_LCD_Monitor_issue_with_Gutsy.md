---
title: "LCD Monitor issue with Gutsy"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by edthompson on 2007-10-18
I have been using Feisty with my LCD TV in my lounge perfectly well. however when I did tried to do a fresh install of Gutsy, my LCD TV monitor displays 'not supported video'.  Thinking it was some issue with the install, I connected the pc up to an old PC monitor to install Gutsy and everything displays fine on the old screen. However when I plug the pc back into the LCT TV monitor it still doesnt work (same message).

As I say, Feisty worked fine with the LCD TV (so did XP and W98 for that matter). I connect via a VGA lead to the onboard graphics on the mobo.

My PC is using onboard graphics on a k7s41 mobo.

My LCD TV is Hyundai Imagequest with the following spec:
 DTV / HDTV Ready: 1080i, 720p, 480p, 480i 
Resolution: 1366 x 768 
Aspect Ratio: 16:9 
Pixel Pitch: 0.2895 x 0.2895mm 
Brightness(Peak): 450 cd/m2 
Contrast Ratio: 1000:1 
Response Time: 23ms 

I have done a checksum and media check an that is all fine.

Does anyone have any ideas?
Many thanks

---

### Post by rogerwn on 2007-10-18
Same issue with my Samsung 1440x900 monitor - 7.10 will only go up to 1024 768!

Gutsy's got a high res screen problem!

---

### Post by Mcavity on 2007-10-18
I have a similar problem with my Hyundai image quest lcd panels at 1280x 1024. If i tell Gutsy manualy what they are it seems to "forget" and I cant get the setting to stick.

---

### Post by Wiebelhaus on 2007-10-18
Crtl+Alt+F2 to drop to console , Log in.

Run

> sudo dpkg-reconfigure xserver-xorg

Manually setup your strange configurations.


Good luck , no worries it easy , just read what it's asking you.

---

### Post by edthompson on 2007-10-21
I tried the xorg suggestion and it was MUCH too complicated for me. I just couldn't get it to work. Such a shame as Feisty worked.  I have moved back to PCLINUXOS. I may well come back for 7.11 if the video issues are resolved.

From the reviews, it seems 7.10 is nearly there; say what you like about XP and Vista but once you have done the updates, it does all work.

It sounds like Gutsy is nearly there. Linux needs a distro that will work for low skilled people who never want to go near a Terminal . At the moment PCLINUX is probably the closest distro to that nirvana but it sounds like Gutsy is virtually there (and with plenty of extra functionality too).
 
Thanks for trying to help.

---

### Post by Mcavity on 2007-10-28
Ok well good news. 
I found the cd that came with the displays I have and managed to get the inf file from that. 
seems to have helped. 
that was not as.. straight forward as I would like.. but I think its progress.

---

