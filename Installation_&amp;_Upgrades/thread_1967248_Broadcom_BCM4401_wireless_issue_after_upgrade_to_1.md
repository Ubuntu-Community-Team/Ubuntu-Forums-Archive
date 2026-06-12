---
title: "Broadcom BCM4401 wireless issue after upgrade to 12.04"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by stisoulreaper on 2012-04-27
First off, I apologize if the answer to this is elsewhere, but I've been looking since the upgrade became official and haven't found an applicable answer.   Now, on to the problem.   I have an older laptop, an inspiron e1705 (a dinosaur, I know) with a broadcom BCM4401 wireless card. 11.10 ran horribly slow, so I jumped on the upgrade ASAP, but I am having nothing but trouble with the wireless. I keep getting a popup asking for my router key in order to authenticate. I enter the key and the wireless connects to the router but ~30 seconds later I get the same popup again.   For the few seconds between asking for authentication, the internet works, but it cuts quickly.   The additional driver utility shows that there are no proprietary drivers in use (though I do seem to recall needing to install the STA driver in the past, but I'm not 100% on that)   All of the workarounds I've found deal with the 43xx chipset, and i've tried the bcmw-kernal source and (out of desperation) the b43-fwcutter.   Thanks in advance, I really want to get this working so I can learn to enjoy Ubuntu again! :)

---

### Post by stisoulreaper on 2012-04-28
Well, it seems I may have solved my problem, and that it was a far more simple issue than I was anticipating! Apparently, when I upgraded to 12.04, the "connect automatically" box (in the editing connection screen) was unchecked. Checking it seems to have solved the issue. A far simpler problem than I was trying to solve, indeed!

---

