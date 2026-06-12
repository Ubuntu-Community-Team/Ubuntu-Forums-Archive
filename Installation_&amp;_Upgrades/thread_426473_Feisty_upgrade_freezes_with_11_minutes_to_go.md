---
title: "Feisty upgrade freezes with 11 minutes to go"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by PaulFXH on 2007-04-28
Running Edgy (dual boot with WinXP) on a HP Pavilion dv1000 laptop.
So, this weekend, I decided to upgrade to Feisty.
Everything seemed to be going fine, all the downloads completed and the installation part was well underway.
Then with just 11 minutes to go, while configuring libgstreamer plugins0.8-0, the upgrade froze. After about 15 minutes of trying various means to encourage it to get going again, I had no option but to pull the plug.
As expected, Ubuntu now won't boot so it looks like I'm going to have to go back to wqhere I started and re-install Edgy.
However, if anybody has any comments before I start, I'd like to hear them.
Thanks
Paul

---

### Post by Cervantez on 2007-04-28
What type of video card and CPU do you have? It's probably an issue with your CPU and Ubuntu's architecture or if you have an ATI card, it may be the problem. The ATI driver for some cards is weird in linux and can cause that kinda thing.

---

### Post by PaulFXH on 2007-04-28
The video card is an integrated Intel 945GM (128MB).
I don't have exact details on the CPU (as it's not my machine and I can't use it all the time) but it's relatively slow at 1.46GHz  (single core)
So, if what you're saying is correct and my CPU is too small or my graphics card is a bit light, I can never install Feisty on this machine?

---

### Post by Cervantez on 2007-04-28
is it an AMD Athlon 64?

---

### Post by PaulFXH on 2007-04-28
The processor, according to the Windows System Information is "x86 Family 6 Model 14 Stepping 8 Genuine Intel 1463 MHz".
Thanks for any further comments you or anybody else might have as I really do want to get to Feisty.

---

### Post by Cervantez on 2007-04-28
Well all I can tell you is to make sure that the version of Feisty you have is the x86 version (PC).

I just realized that you said you were doing an upgrade... I wouldnt' recommend that at all. Just back up your important stuff and do a fresh install, it's more likely to work.

If that doesn't work, maybe the CD was a bad burn. Check the MD5 sum for your download and reburn it if you want, see if that helps. It's worked for me before.

---

### Post by PaulFXH on 2007-04-28
Thanks again.
However I've seen many posts from people who said they upgraded to Feisty without any problems.
Antway, fresh installing is now my only option as the OS I had has been hosed (or rendedred un-upgradable).
Nevertheless, it would be interesting to hear from anybody who might have some idea what might have gone wrong with my attempted upgrade to Feisty. I refuse to believe that I'm the only one this has ever happened to although, in googling around, I didn't find anything exactly similar.

---

