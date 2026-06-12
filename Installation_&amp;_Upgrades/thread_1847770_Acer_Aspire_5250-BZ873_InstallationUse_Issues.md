---
title: "Acer Aspire 5250-BZ873 Installation/Use Issues"
date: 2011-09-21
forum: Installation &amp; Upgrades
---

### Post by AlexNagy on 2011-09-21
Had amd64 Ubuntu installed (dual core AMD C-50, assumed it was 64-bit), system locks up randomly. Created a i386 boot usb stick using the disk creator on a Toshiba Satellite running 11.04, try to go back to Acer to boot off of it. Get to boot load screen, select language, select install ubuntu, goes to boot into the system instead of install process.

I'm about to grab my Gentoo livecd and toast the harddrive and start from scratch. Would rather not but will if I have to (still going to put Ubuntu on the lap top, it's for a guy who  used to use Windows). I've installed (successfully) Ubuntu on 6 computers, two of them laptops. This is the only computer really giving me fits. Any ideas? Anyone else having the same issues?

---

### Post by AlexNagy on 2011-09-21
bump

---

### Post by AlexNagy on 2011-09-26
hack fix: selected the athereos network boot agent as first boot device and has no lockup issues for rest of use.

---

### Post by ttanev on 2011-09-26
Hi there, got the same machine in my hands and I'm typing this from the live USB while installing it :)
Thanks for the hack-fix, I'll try to install 11.04 x86_64. The thing that makes no sense is there's no wi-fi activity and no networks at all and Fn+F3 doesn't do anything. Guess I'll have to wait for the installation to finish and look after that. There's no hardware on/off button.

Edit: Actually that model is Acer 5250-C52G32Mikk

---

### Post by AlexNagy on 2011-09-26
Good luck man. This Acer had wifi from the go (I think). I'm kind of annoyed by this hack-fix because I'd been telling this kid about how great Ubuntu is (he's impressed by the rest of it and we're both convinced it's a hardware issue...).

---

### Post by ttanev on 2011-09-27
Almost everything worked out of the box after install /camera, internal mic, function buttons, CPU scaling, etc./, I had no lockups but maybe it's related to the BIOS update I made to 1.05 / from 1.01/. The Wi-Fi performance is still awful /can't connect, lots of losses and bad signal ratio/ even with 3.03 kernel, but with no lockups.
I tried to install the proprietary Catalyst driver for the integrated radeon, but it was lacking standby functionality, so went open source driver with automatic power management solution from here - [http://ubuntuforums.org/showthread.php?t=1811178](http://ubuntuforums.org/showthread.php?t=1811178) Got almost an hour more battery life that way, but less working titles from the Humble Indie Bundles, though. :) 
Tried 11.10 beta2 for Wi-Fi too, but with no luck.

---

