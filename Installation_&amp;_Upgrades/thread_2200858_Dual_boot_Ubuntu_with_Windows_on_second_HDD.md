---
title: "Dual boot Ubuntu with Windows on second HDD?"
date: 2014-01-21
forum: Installation &amp; Upgrades
---

### Post by lukeborley on 2014-01-21
Hi, apologies if this is already covered elsewhere but I'm still very much a Ubuntu beginner and need all the help I can get. Basically, I moved to Ubuntu after my old XP desktop got a particularly egregious driver problem last year and have been using it ever since then; I've even moved to a new PC I bought deliberately without an OS figuring it was much better hardware for the money and Ubuntu is generally fine for all I want to do.

But, there are still a few things I used to be able to do in Windows XP that I haven't been able to in Ubuntu, even in WINE. Running certain games. Ripping hardcoded subtitles. The e-learning for my work website that insists you need to run IE. So, I figured it would be good to have XP  (or possibly Windows 7 or 8) as a dual boot option alongside Ubuntu 13.10. I even have a spare, completely formatted 300GB SATA harddrive set aside for the purpose. But, I've had 13.10 installed for some time and am reluctant to have to wipe it and go through the tedious process of reinstalling all my utilities and Steam library and stuff if I can help it. 

As it stands, when I've tried the Windows install disc it doesn't recognise the formatted second harddrive - presumably this is something to do with Ubuntu being installed already on the main drive. I've read that it's much easier to install Windows first and Ubuntu after, but as I say, I'd rather stick with my comfortable hoard of recent Ubuntu clutter if possible. I've started to think it might work if I open my computer case and temporarily disconnect the main harddrive (housing Ubuntu) so that only the secondary 300GB drive is connected and then try the Windows install on that. But from what I understand Windows would overwrite the boot sequence then and I'd have to reinstall Ubuntu anyway? Is that right? Sorry for the noobishness.

---

### Post by k-neko on 2014-01-21
Firstly, 
You could use VMWare or virtualbox as a solution for your Windows neediness. It would include some of old games, too (that don't require too much 3d and shininess).


Secondly, if you will disconnect your Ubuntu hard drive, you won't lose your bootloader on it. Thus, Grub bootloader won't be overwritten by windows, and you will be able to boot Ubuntu upon connecting your hard-drive back again.
However, depending on your BIOS, with initial setup of 2 drives & removing 1st of them later, connecting it back won't make it bootable, e.g. you will have to change boot priorities after installing your Windows & connecting your Ubu hdd back again.
Also, I'm not sure (never dualbooted a thing), but you probably will have to re-configure your grub for it to see your newish windows installation.


Thirdly, I'm almost 100% sure that you won't be able to install XP on new hardware due to that EFI mumbo-jumbo.

---

### Post by oldfred on 2014-01-21
If new computer I would not install XP. XP is about to expire and does not have drivers for many of the features with new systems. 

If installing a newer copy of Windows you do have to know if you installed Ubuntu in UEFI or BIOS boot mode and then install Windows on the other drive in the same boot mode.

---

### Post by lukeborley on 2014-01-21
Short story, success! Thanks! 

Longer story: after the Windows install I reconnected the primary drive and used that Boot Repair utility, then found that Ubuntu couldn't connect to the internet any more. Eventually I had to do a re-install (keeping all the clutter) from a 13.10 live disc, and after that I found that my sound card and keyboard and second monitor weren't recognised any more. But with a fresh install of updates everything works now. Thanks!

---

