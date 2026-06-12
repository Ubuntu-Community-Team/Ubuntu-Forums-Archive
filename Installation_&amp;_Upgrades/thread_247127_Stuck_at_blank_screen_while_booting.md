---
title: "Stuck at blank screen while booting"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by Dynamis on 2006-08-30
Hi, I put this in the install section because i've just installed, and this happened on the first attempt to load the installed system. It also happened when i tried to boot from the Live CD.

The system seems to load normally, I see the loading screen with progress bar. That seems to complete, then it switches to a blank screen with a flashing cursor. About 2 seconds later, the screen appears to actually switch off. Just after that, I hear a musical chime.

If I press the power button, the screen re-appears at the login stage and immediately begins the shutdown sequence.

I realise my problem is probably related to it being a laptop, but I'm hoping I can get some tips.

I tried both the Live CD and the alternate install. The problem stopped the Live CD from even booting up. The alternate install went without a hitch, but i get this problem when trying to boot (at the same time as with the Live CD).

I previously tried installing Gentoo linux. I had to use the "noacpi" boot option to get that to boot, but it didnt solve this problem. I didn't manage to get Gentoo working in the end (im no linux guru) so I decided to try Ubuntu.

System:

Acer TravelMate 8104WLMi.
Pentium M 760 (2.0Ghz)
15.4" WSXGA+ TFT (widescreen)
ATI Mobility Radeon X700
1GM RAM
100GM SATA HD

Thanks in advance,

Dynamis

EDIT: Found a hint on the wiki [https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire1694WLMi]("https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire1694WLMi") so i'll try that now.

EDIT the 2nd: Yep, that fixed it. Sorry to bother you all.

---

### Post by WhiteHorse on 2006-10-20
That link you posted is broken. I haven't found a fix for this yet. I think it's the ATI X700 I have is trying to go to the VGA port rather than the laptop display...

---

