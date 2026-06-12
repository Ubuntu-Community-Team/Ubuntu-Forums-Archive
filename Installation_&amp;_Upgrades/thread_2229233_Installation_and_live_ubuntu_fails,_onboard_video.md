---
title: "Installation and live ubuntu fails, onboard video"
date: 2014-06-12
forum: Installation &amp; Upgrades
---

### Post by micwit2 on 2014-06-12
I want to try and move from windows to ubuntu as my primary OS after having played with it a bit on an old laptop I have. I have just built a new machine for my primary work machine, and figured this is the time to give it a go. The main specs on the machine are:
MB - Gigabyte GA-H97-DH3
RAM - 32GB Kingston DDR3 1600
Video - Gigabyte geforce GTX 750 2GB GDDR5
CPU - i5 4690 (3.5GHz Haswell)
SSD - Samsung 250GB 840 Evo
If there is anything else you think may affect it let me know.

So basically, I have tested ubuntu 14.04, 14.04b2, 13.10 and 12.04 (all 64-bit) on DVDs as well as 14.04 on USB. The results are all pretty much the same, either sits on a black screen, or stays on a screen with the cursor flashing after the initial splash screen. When I press the up button on the initial splash screen, I get to the language and other options section. I tried enabling all the other options (from what I read online, nomodeset can help), and the loading screen comes up (and if I press esc I can see the modules loading etc), then the cd drive reads on and off for a while. I figured it may be running in the background (I had selected the live version), so I pressed ctrl+alt+t to open a terminal and typed sudo reboot, and the cd read for a bit and then ejected! So Im guessing it is actually running in the background! Brightness of the monitor is already at 100%.

Any ideas?

Thanks


Quick update: I just set the bios to boot to the onboard video card, and booted into the live cd, and it all works! So it appears to be the GTX 750 thats the problem. Any ideas?

---

### Post by micwit2 on 2014-06-12
OK, problem solved! I won't go into all the details of how I found this out, but trust me, DISABLE YOUR ONBBOARD GRAPHICS! For some reason, even if your card is set to default in the BIOS, ubuntu will just use it as default anyhow! So you won't realise it, but you probably actually have the first screen loaded on your onboard video card!

Of course, when you do this, ensure your nvidia card is working correctly:
1. Boot into BIOS and check the card you want to use is set as 1st priority. If it is not, change that and reboot
2. When you are viewing the bios through the card you want to use, disable the onboard video.

That way you won't disable the onboard video and AFTER this realise there is something wrong with your card. Doing it this way, you can at least go back into the bios and enable your onboard card.

Once you have disabled your onboard card, load of the CD or USB. If the screen goes black for a bit, give it a minute or 2 (I find that it takes a bit longer with a card than onboard to get to the first screen, Im guessing ubuntu is working out what divers to use), after a minute or 2, the mouse should appear and the rest of the boot should go ahead as expected!

---

