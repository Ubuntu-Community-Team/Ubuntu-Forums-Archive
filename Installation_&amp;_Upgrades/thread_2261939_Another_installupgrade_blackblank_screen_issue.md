---
title: "Another install/upgrade black/blank screen issue"
date: 2015-01-22
forum: Installation &amp; Upgrades
---

### Post by markhagen72 on 2015-01-22
hi folks,
I'm having issues installing any of the new 'buntu versions beyond the 14.04 LTS on a new Asus Zenbook UX305fa. They all (using live usb - I've used most available methods to make them) boot up, go through grub and then the screen goes blank (i.e. it's on but "black" - I'll use the terms interchangibly). Using nomodeset and/or recovery I can get into ubuntu proper but haven't been able to find a working solution beyond what follows below on kernels. I know that ubuntu is actually "there" behind the blank screen because if I send the laptop to sleep (f+F1 in this case) and wake it back up, I see the GUI for a split second before it drops back "behind" the black screen (in Mint I can hear the startup pingsound). Same happens if I upgrade 14.04LTS.

Testing on Mint 17.1 (in recovery), I tested backwards through the kernels. I knew the 14.04LTS "base" 3.13.0-32 works fine, Mint starts with 0-37 and now I've nailed it down to 0-34 that works and as of 0-35 the above bug comes up again. I'm leaving it to 0-34 for now I suppose - regular updates will continue to work, right?

Having perused a myriad of sites & forum entries (yes, the stick too) I can't find a reason/solution for this behaviour directly - maybe I've just overindulged and can't see the forest for the trees?
Thanks for any thoughts :)

---

