---
title: "Asus K52JC Optimus (nvidia disabled) But still can't get X to work"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by enricribas on 2010-11-23
I am at a loss and would really appreciate any help. I have tried for 5 days to install Ubuntu using forum tips from everywhere. I have installed Ubuntu on 5 other machines with no problems but I bought a new ASUS K52JC with nvidia optimus and I am stumped.

I am installing along side Windows 7 (not that it matters, I guess). I still need it for Spaceclaim and Google Sketchup. :(

I disable the nVidia card in the BIOS because I read that Ubuntu does not have Optimus support. Fine. I will use the Intel card that is integrated. I can deal with that. 

Then using the LiveCD (10.10), I can boot to Ubuntu with no problems and I have 1366x768 resolution. All seems good. So now I install Ubuntu. All seems fine. When I reboot the computer and try the first option (Ubuntu), I only get to the text-only terminal screen. Running "X" once logged in gives me a blank screen. The logs say "FATAL ERROR, screen not found". Running "startx " works but of course using generic graphics driver and only at 1024x768 (and it looks bad). Running "lspci" shows that it is using "intel".

I have tried running with "nomodeset" and every variation I could think of. 

Running Ubuntu with BIOS setting to allow nvidia card locks up the startup at "STACK" with a bunch of hex numbers, so that's a no go. 

I have no xorg.conf anywhere when I boot to terminal or startx. Not sure if it's needed. It can't find it either with LiveCD running. Not sure if it's needed. I don't have any nvidia drivers. I even tried removing all packages with "nvid*". No luck. 

I am about to give up and possibly return this computer, which makes me sad. 

I am not Ubuntu expert, so any clues would be appreciated. Might try another distro but would rather not. 

Thanks in advance to anyone willing to help.

---

### Post by enricribas on 2010-11-23
I am still trying to install/reinstall Ubuntu 10.10

I have an error with intel drivers I believe. My X error logs show 
"intel(0): No Kernel modesetting driver detected" when booting.

Is there any way of updating intel drivers?

I am not getting a lot reads on this? Is my title not interesting enough. :)

I have also tried "sudo X -configure" to generate a new xorg.conf file but to no avail. 

I have until Friday to be able to return this laptop and am hoping someone can help. 

Thank you very much.

---

