---
title: "Installing with windows 8 - windows starts right after boot"
date: 2014-04-25
forum: Installation &amp; Upgrades
---

### Post by Nick_Halden on 2014-04-25
I'm trying to install ubuntu on my machine (Trying to make dual boot with windows 8) and I'm having some problems.
I know there are tons of discussions in the subject, and I searched them but couldn't find an answer.
Whene I reboot the machine, I have the first windows where I can go to the bios, but after that windows is automaticly starts, even thogh I have the live-usb inserted.
The bios is Phonix SecureCore Tiano, I put the usb generic first in the priority in the bios, and the UEFI boot support is disabled. The fast start up from within windows is also disabled, and I can't find anything else in the bios that can help me.

Any suggustions how can I install the ubuntu?
Thenks for the help.

p.s. I made the live-usb with the universal-installer.

---

### Post by ronb19495 on 2014-04-25
first off insert your usb with ubuntu on it then reboot,when rebooting open bios look at boot menu in bios you might have to usb entries one is standard boot the other is uefi if your machine is uefi able.select either standard usb or uefi usb select save,reboot you should see a screen try ubuntu or install ubuntu,select your desire hit enter and it should be all good.be aware if you have to reboot go back in bios and do again.now if you have installed ubuntu boot your machine go into bios boot options check whats in your first boot choice if you have windows 8 you should see windows boot manager as 1 option there will be a hard drive option and should be a ubuntu option if so chosse ubuntu make it first boot priority save your choice and reboot,you should get a boot screen with ubuntu then other options for ubuntu then windows choose ubuntu and it will boot into ubuntu if you want windows just arrow down to windows hit enter and windows should boot .ubuntu just becomes the boot manager for ubuntu and windows good luck i just googled your bios it is uefi capable if I where you I would enable uefi as windows is uefi I have windows 8 and ubuntu 14.04 and they travel along fine in uefi mode but thatd your choice
regards Ron
just a quick question are you using seperate hard drives or only one if you have only one hhard drive it might be a good idea to shrink windows partitition and partition remaing free space as it will help ubuntu install easier also windows 8 partitions hard drive as GPT it is for uefi for windows so ubuntu will install on GPT inuefi mode
use gparted to partition your drive as it is user friendly it will be on your usb instalation stick

---

### Post by oldfred on 2014-04-25
Some UEFI/BIOS have settings to enable USB ports or to select whether they even can boot at all.

And some have a password to open up extra settings. But do not ever forget password as otherwise you may not be able to change anything in the system in the future.

---

### Post by WoodenWalker on 2014-04-25
W8 likes to go into a hibernative state instead of truly shutting down, it seems. When in Windows type 
"Shutdown /s /t 0" in the command prompt to truly shut down. Then enter the BIOS on boot and try to boot from USB there. Check oldfred's recommendation as well. I haven't personally heard of that, but he is far more knowledgeable than I am.

---

### Post by ronb19495 on 2014-04-26
heres how you bios boot probably looks like and if ubuntu installed on the hard drive correctly it should have ubuntu in there as well

---

### Post by Nick_Halden on 2014-04-26
Thenk you for all your replays. Somehow I used another USB and it worked (the first USB works on the computer, just somehow not in boot, weird). Thenk you very much for your help.

---

