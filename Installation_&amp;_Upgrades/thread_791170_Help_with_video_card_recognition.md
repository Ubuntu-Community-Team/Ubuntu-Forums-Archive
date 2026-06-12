---
title: "Help with video card recognition"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by jecastellon on 2008-05-11
Hi

This may seem lame to you, but I've been using Ubuntu for about a year now (user level) and now I have a problem that I really can't solve by myself. Now let me get straight to the point:

I own a Voodoo4 graphic card and I'm using a Samsung SyncMaster 551v screen (I can't afford to change them, so upgrading my computer is not an option, lol).

The thing is that when I installed UbuntuStudio 7.04 last year, it recognized my card and screen so well, that I never had a problem with the configuration. Then I upgraded to 7.10 and it stayed that way, until I did something wrong and had to format some days ago. But when I installed version 8.04 from scratch, it can't recognize my screen on 1024x768 (the higher possible resolution is 800x600).

I've tried installing all three releases of Ubuntu, Kubuntu and UbuntuStudio (7.04, 7.10 and 8.04). Obviously, I've also tried to change the settings on xorg.conf (looking up the refresh number for my screen on the manual and all), but everytime I did it, I ended up loosing total vision of the screen and, because I can't change it back without seeing, I had to reinstall Ubuntu all over again. I've also tried re-installing libglide3.

Then I said to myself "ok, so I'll install 7.04 again and upgrade from there", but I guess two upgrades is too much for the O.S. so it crashed and/or got extremely bugged both times I tried it.

Today I installed 7.04 again and decided not to upgrade at all, but somehow the system looses a couple of functions, the most important being that, besides I configure my internet connection properly with pppoeconf, it just won't connect again on startup (and it even disconnects by itself). The only way to solve that is to configure pppoeconf again, disconnect manually and then connect again in the terminal using pon/poff dsl-provider. This is also one of the things that happened when I tried to upgrade from 7.04, so I guess is a problem of obsolete software.

So, I need help in one of two issues:

1.- How is it that the install program of UbuntuSudio 7.04 configured my video card and screen all by itself? Is there a configuration file that is missing in the other releases (then why, I answer)?... Can I make the same configuration on 8.04, maybe installing some missing package that UbuntuStudio 7.04 had (I don't mind installing the original Ubuntu, but it never recognized my card)? Or there is another way of configuring Ubuntu for it to accept a resolution higher than 800x600 with my card and screen?

2.- If nothing of that is possible or even works, How can I fix that internet connection problem that appeared now? Why is the system modifying my connect information file (if that is what it is doing)?

I'd really appreciate if you can help me, because believe me... I have spent a lot of time trying to do it by myself without results!!

Thanks a lot!!

---

### Post by RJARRRPCGP on 2008-05-11
That sucks. Your disconnects remind me of the days of POTS and finicky POTS modems. :( 

Also, I'm on the same boat as you, but fortunately was able to get an AGP-based GeForce 7600 GS back in November for my other PC. 

The PC I'm typing this from is in the sig. ;)

---

