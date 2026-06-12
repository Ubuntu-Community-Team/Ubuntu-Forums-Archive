---
title: "Jaunty Beta Graphic problem with awn"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by aml1648 on 2009-04-09
Hello,

Since upgrading my dell inspiron 1525 to Ubuntu Jaunty Beta, the os has "crashed" 3 times: the keyboard would suddenly become totally unresponsive. I can still move the mouse cursor without any problem but cannot click or right click on anything.

I had to turn off the computer and restart each time. 

It seems that this situation occurs when the system tries to run something that is particularly graphic intensive, i.e. displaying full blown flash ad.  
I have the standard inspiron 1525 graphic card and run avant window manager,compiz fusion (rotating cube, water effects etc.) and emerald with extra effects enabled.

My graphic card is Mobile Intel(R) 965 Express Chipset Family with 358 MB of total graphic memory (128 MB of Dedicated system memory 128 MB plus 230 MB of Shared system memory 230 MB) 

Is this a bug or maybe the graphic demand is too much for my graphic card?.

Thanks!

---

### Post by balaknair on 2009-04-09
It's likely to be a bit of both. Intel graphics has some issues with the new Xorg and the new Linux kernel, the Xorg_Intel drivers are as of now buggy. Though the devs at Intel are working on it, some of the stuff in the new drivers(which aims to improve graphics performance and capabilities) is not quite finished yet. Hopefully we should see some patches that fix the major issues released by the time Jaunty goes RC. And the next major release of the Intel drivers this summer will(I hope) fix the regressions.

PS: I've got a GMA based on the same chipset with similar specs, but the only issue I've had was with the Awn 'Shiny Switcher' applet. The applet would crash, but both Awn and the desktop were just fine. This was supposed to be a bug in the applet.

---

### Post by aml1648 on 2009-04-09
Hi balaknair,

Thanks for your highly informative reply. I hope that this problem would go away/alleviate with the official release of Jaunty later this month.

BTW,I too have experienced the problem you described.

So if my system crashes again, is there anything else I could do beside shutting down the computer with the power button?

---

