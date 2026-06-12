---
title: "Graphics and GUI no longer supported after upgrade?"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by NFITC1 on 2010-03-01
The last time I updated Linux it was from Gibbon to Heron. (so 7.10 to 8.04 :( ) I'm now trying to get caught back up. Thing is, now that I updated from 8.04 to 8.10 I can no longer get to a GUI. Also, most of the text in the terminal is a diamond character as if the font that's installed doesn't want to work most of the time. This is somewhat confusing, but I believe my system's language was set as Japanese before the upgrade and now it's trying to display Kana and/or Kanji and the terminal doesn't like that. Not really important, but I'm not sure how to proceed to the next upgrade or get to a GUI. Fortunately, my system's set up to dual-boot with windows. Can someone help tell me how to get my GUI back or what package to install?

I'm running on a laptop with an ATI mobility Radeon 9700. I've had problems with it and drivers in previous versions back to 6.10 too, but never to the point that the GUI wouldn't work.

UPDATE:
It's actually an issue with my X Server. I tried "startx" and it says "No Screens found". I looked in my xorg.conf file and there are two screens listed at the bottom. It produced a log too, but I can't get my Flash drive to mount so I can't say exactly what it says. It did mention that there were a lot of font directories that didn't exist along with a few other warnings.

---

### Post by Mark Phelps on 2010-03-01
Just so you know ... that card is not supported with ATI drivers in any Ubuntu version newer than 8.10.  So while you may be able to eventually upgrade to 9.10 (or even, 10.04), you will need to use the default open source drivers for 9.04 and newer.

---

### Post by NFITC1 on 2010-03-01
> **Mark Phelps said:**
> Just so you know ... that card is not supported with ATI drivers in any Ubuntu version newer than 8.10.  So while you may be able to eventually upgrade to 9.10 (or even, 10.04), you will need to use the default open source drivers for 9.04 and newer.

[s]I had thought about that, but I also thought the support stopped after 8.10 was released. Where can I get the open source drivers?[/s]

OK, I got past this by changing the driver from ati to "radeon". Now I got all the way to Koala and I'm getting a blank screen after "startx". It's not giving me an error, but when I push the power button to turn it off I see the white ubuntu icon as it's shutting down. Any one have a suggestion about what I can do?

---

