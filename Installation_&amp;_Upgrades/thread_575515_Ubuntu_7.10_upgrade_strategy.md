---
title: "Ubuntu 7.10 upgrade strategy"
date: 2007-10-14
forum: Installation &amp; Upgrades
---

### Post by FSHero on 2007-10-14
Hi there everybody,

I've got a few questions on upgrading to Kubuntu 7.10 from 7.04.

Firstly, I've heard that upgrading can "break" certain devices: e.g. wireless network card. Currently, I'm using the module: rt2570 for my wireless network card. (I don't know the brand, it came with my computer. It seems to present as a USB device rather than a PCI device in lspci -v, in Windows, etc.)

I'm thinking of using a Live CD to try out the new Kubuntu -- but after confirming that everything works, I will do an upgrade from Adept.

I have an internet connection from Sky Broadband :P. However, I have a monthly download limit of 40 GB. I wanted to know: will the upgrade be very large? I mean, will every single package that I have insalled already be re-downloaded? Or will only the ones that need upgrading be upgraded?

To complicate matters slightly, I have two computers sharing this internet connection. Unless the download is relatively small (less than 1GB per computer), I would prefer somehow getting all the packages in one go, so that it doesn't eat into my limit too much. I was thinking about using the alternate-cd to do the upgrade, after testing Gutsy out with the live CD. Does anyone recommend this?

Finally: I was wondering when the best time to upgrade is! In April 2007, I was eagerly awaiting Feisty. But I could not get to the Ubuntu homepage [www.ubuntu.com](www.ubuntu.com)! It must have been flooded with requests. (I was planning to download it through BitTorrent, anyway, just as I plan to do with the Gutsy CDs.) I would like to avoid the initial "rush" of people trying to download. How long should I wait after the release day to do my downloads?

Thanks to everyone in advance. Great community, great development team... great product!

--FSHero

---

### Post by FSHero on 2007-10-14
I forgot to mention... I have proprietary NVIDIA graphics drivers installed... according to [this  thread](http://ubuntuforums.org/showthread.php?t=379969&highlight=ubuntu+upgrade+strategy), NVIDIA drivers will break with every kernel install.

How should I get around this? Switch to driver "nv" temporarily? Or just disable the NVIDIA proprietary driver through restricted-manager?

---

### Post by jjcv on 2007-10-15
Ubuntu is pretty good with NVIDIA drivers.  It will try and load the restrictive driver for you and if your card is pretty recent it will probably just work.

If you have an older card you may need to install the legacy drivers or go to the Nvidia website and install the driver appropriate for your card.   Have a look at the message logs after your install and it will give you a good idea of what to do or get.

---

### Post by FSHero on 2007-10-15
Thanks jjcv,

So... should I just leave everything on my 7.04 system as it is, or should I disable the NVIDIA proprietary driver through restricted-manager before upgrading?

---

