---
title: "Installer not detecting SATA drives"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by UniverseA7X on 2008-07-18
I built a computer for a friend a couple days, and he wants Ubuntu on it. 

I have tried several discs, and they all do the same thing.

He has an SATA DVD and HDD drive. They are both recognized in the bios of the moboard. But the installer doesn't want to recognize either one and asks for drivers. We had to harvest and Ancient IDE cd drive from an old compaq he had in order to get past the "Detect CDROM drive" step. It went past, but now it doesn't detect the SATA HDD. I'm lost. Does anyone know what's going on?

Thanks.

Brandon

---

### Post by hansdown on 2008-07-18
Just a guess, perhaps you need to update, as the developers do a bang-up job of fixing things that I don't comprehend.

---

### Post by UniverseA7X on 2008-07-18
> **hansdown said:**
> Just a guess, perhaps you need to update, as the developers do a bang-up job of fixing things that I don't comprehend.

Update what? The computer doesn't have an OS at all right now.

---

### Post by coffeecat on 2008-07-18
Could you post details of the motherboard and the chipset it uses? You have to be very unlucky for there to be no kernel drivers for your sata interface, but I've read of people having problems with brand new bang-up-to-date chipsets. It takes time for the kernel maintainers to include new drivers, and for these to trickle down to the various distros. I have no experience of SATA optical drives but I've read of problems with some of these - again down to lack of drivers yet.

I'm afraid I'm unlikely to be able to take you any further. Just thought I'd give you a pointer. On the few occasions I've built my own machine I've always taken the precaution to use a motherboard with a chipset that's not on the bleeding edge and I've not had these sort of problems 

> **UniverseA7X said:**
> But the installer doesn't want to recognize either one and asks for drivers.

Which CD are you using, the live CD or the alternate? Is this a text message you get before the GUI loads up? When you used the old ide optical drive, did you manage to get into the GUI desktop? Not that any of that helps much, but it's useful to get the full picture.

---

### Post by coffeecat on 2008-07-18
> **UniverseA7X said:**
> I built a computer for a friend a couple days, and he wants Ubuntu on it.

I've just had another thought. Consider it a continuation of my previous post.

Which version of Ubuntu were you trying, the latest 8.04 or an earlier? If my hunch about kernel drivers is correct, then you need the latest version to have any chance.

Also, it's just possible that another distro may have incorporated the drivers where Ubuntu has not. Hardy Heron is using the 2.6.24 kernel whereas openSUSE is using 2.6.25. Mandriva 2008 Spring is using the 2.6.24 kernel but may have patched it with extra drivers. Both of those distros do live CDs. I realise your friend wants Ubuntu, but it might be worth a try.

---

### Post by UniverseA7X on 2008-07-19
> **coffeecat said:**
> Could you post details of the motherboard and the chipset it uses? You have to be very unlucky for there to be no kernel drivers for your sata interface, but I've read of people having problems with brand new bang-up-to-date chipsets. It takes time for the kernel maintainers to include new drivers, and for these to trickle down to the various distros. I have no experience of SATA optical drives but I've read of problems with some of these - again down to lack of drivers yet.

I'm afraid I'm unlikely to be able to take you any further. Just thought I'd give you a pointer. On the few occasions I've built my own machine I've always taken the precaution to use a motherboard with a chipset that's not on the bleeding edge and I've not had these sort of problems 



Which CD are you using, the live CD or the alternate? Is this a text message you get before the GUI loads up? When you used the old ide optical drive, did you manage to get into the GUI desktop? Not that any of that helps much, but it's useful to get the full picture.

Gah. I'm not sure what chipset it is or exactly what motherboard it is. I know it's a newer MSI moboard with 45nm support. The computer isn't right in front of me at the moment, So I'm not entirely sure.

I used both the live cd and text installer. The Live CD worked great in the old IDE drive. The installer disc got past the CDROM detection, but when it got to the partitioner, it couldn't find the HDD. Same on the live cd. The GUI installer showed up, but once it got to the partitioner, there were no hard disks listed.

> **coffeecat said:**
> I've just had another thought. Consider it a continuation of my previous post.

Which version of Ubuntu were you trying, the latest 8.04 or an earlier? If my hunch about kernel drivers is correct, then you need the latest version to have any chance.

Also, it's just possible that another distro may have incorporated the drivers where Ubuntu has not. Hardy Heron is using the 2.6.24 kernel whereas openSUSE is using 2.6.25. Mandriva 2008 Spring is using the 2.6.24 kernel but may have patched it with extra drivers. Both of those distros do live CDs. I realise your friend wants Ubuntu, but it might be worth a try.

I'll download mandriva and openSUSE right now. I don't think he'll mind. He just wants to use his computer right now. haha.

---

