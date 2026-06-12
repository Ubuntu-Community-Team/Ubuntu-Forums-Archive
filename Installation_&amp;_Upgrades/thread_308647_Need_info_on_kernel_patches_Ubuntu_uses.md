---
title: "Need info on kernel patches Ubuntu uses"
date: 2006-11-28
forum: Installation &amp; Upgrades
---

### Post by darkshadow on 2006-11-28
Ok 2 days ago I self compiled kernel 2.6.18-ck1 (used edgy's amd64 .config with no changes) and since then I have lost the ability to suspend-to-ram my laptop (Acer Travelmate 4404) which always suspended perfectly under Ubuntu kernels. I was wondering what patches Ubuntu Edgy used on the Vanilla kernel that I could try to get suspending back since I miss it.

So far that is the only downside to self compiling is loss of suspending as it now locks up my laptop to the point of the power button not working and I have to pull the battery and ac adapter to do anything)

My bonuses to the new kernel are
1. Edgy works perfectly stable (used to lock up 3-4 times a day for no reason including fresh boots where I never touched the keyboard or mouse)
2. I no longer have to use special boot parameters to get my wireless card working
3. My card reader is now capable of using 2GB SD cards

---

### Post by darkshadow on 2006-11-29
Well I finally got the best of both world with Ubuntu patches and a newer kernel version. I just got the bright idea to go into the repositories and grap Feisty's 2.6.19 kernel source package and its .config from the image package. I compiled it and I am running it right now. On my Edgy install

My final tally

Pro list
2GB SD card works
Faster bootup
Suspend works again
First keyboard press of bootup is not lost to nothingness

Oh well list
I had to go back to using boot parameters to use wireless (must be from one of the patches Ubuntu uses)

I have yet to see if it is as stable as my 2.6.18 compile as all the problems I had with freezing with edgy's kernel could be from Ubuntu's patching like my need for boot parameters

---

