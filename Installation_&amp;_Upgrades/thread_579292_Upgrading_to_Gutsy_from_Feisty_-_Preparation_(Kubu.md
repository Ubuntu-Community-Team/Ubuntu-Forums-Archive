---
title: "Upgrading to Gutsy from Feisty - Preparation (Kubuntu)"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by c_martini on 2007-10-18
In anticipation of the official Gutsy launch, I would like to prep my machine for the upgrade from Kubuntu Feisty to Kubuntu Gutsy.

My check points / questions are as follows:

1. **nvidia-glx-new** driver: Does this need to revert to the '**nv**' driver before upgrade?

I have had a problem by where something is amiss in my **xorg.conf** and the kdesktop always loads with the incorrect resolution (640x480). I always have to open the **nvidia-settings** and change resolution to 1400x1050 or 1280x1024 and apply the settings manually after every reboot (have tried this with root as well and still does not save the settings, yet my xorg.conf looks fine). Should I also scrap my xorg.conf and let the upgrade take me into shiny new **bulletproof-x** to sort out my xorg.conf?

2. **ntfs-3g** driver: Since Gutsy now includes this, should I remove this as well and backup/remove my **fstab**?

3. **sources.lst**: This of course has all my additional repositories for all the extra bits I have installed over the past several months. How should I strip this down to ensure the smoothest upgrade possible?

4. **Firefox**: I have the **Swiftfox** variant installed with some plugins, including **Flash**. Since  Gutsy now includes a new method for installing some common firefox plugins and flash, should I remove Swiftfox or any of its associated plugins?

5. **ALSA** driver: I have compiled from source and installed the latest version for my kernel version (linux 2.6.20.16-generic) with a custom .asoundrc config for my m-audio revolution 5.1. Should I remove ALSA and backup my **.asoundrc**?

I think those are most important changes I have made from the default Kubuntu Feisty install, aside from all the usual updates. Any suggestions appreciated.

BTW: I have had a glance at the official upgrade procedures as well..

 ???

---

### Post by c_martini on 2007-10-18
bump:: anyone?

---

### Post by frenchcr on 2007-10-18
> **c_martini said:**
> In anticipation of the official Gutsy launch, I would like to prep my machine for the upgrade from Kubuntu Feisty to Kubuntu Gutsy.

My check points / questions are as follows:

1. **nvidia-glx-new** driver: Does this need to revert to the '**nv**' driver before upgrade?

I have had a problem by where something is amiss in my **xorg.conf** and the kdesktop always loads with the incorrect resolution (640x480). I always have to open the **nvidia-settings** and change resolution to 1400x1050 or 1280x1024 and apply the settings manually after every reboot (have tried this with root as well and still does not save the settings, yet my xorg.conf looks fine). Should I also scrap my xorg.conf and let the upgrade take me into shiny new **bulletproof-x** to sort out my xorg.conf?

2. **ntfs-3g** driver: Since Gutsy now includes this, should I remove this as well and backup/remove my **fstab**?

3. **sources.lst**: This of course has all my additional repositories for all the extra bits I have installed over the past several months. How should I strip this down to ensure the smoothest upgrade possible?

4. **Firefox**: I have the **Swiftfox** variant installed with some plugins, including **Flash**. Since  Gutsy now includes a new method for installing some common firefox plugins and flash, should I remove Swiftfox or any of its associated plugins?

5. **ALSA** driver: I have compiled from source and installed the latest version for my kernel version (linux 2.6.20.16-generic) with a custom .asoundrc config for my m-audio revolution 5.1. Should I remove ALSA and backup my **.asoundrc**?

I think those are most important changes I have made from the default Kubuntu Feisty install, aside from all the usual updates. Any suggestions appreciated.

BTW: I have had a glance at the official upgrade procedures as well..

 ???

First sudo apt-get autoclean

1. No, just leave it as it is.
2. No let gutsy do the work for you.
3. sudo cp sources.lst sources.lst_feisty, then let gutsy change sources.lst and copy paste from feisty backup you made
4. If you did this with automatix remove them and remove automatix, else just take your chnces, you dont have to remove anything.
5. This may get configured for you, im not sure.

---

### Post by c_martini on 2007-10-18
> **frenchcr said:**
> First sudo apt-get autoclean

1. No, just leave it as it is.
2. No let gutsy do the work for you.
3. sudo cp sources.lst sources.lst_feisty, then let gutsy change sources.lst and copy paste from feisty backup you made
4. If you did this with automatix remove them and remove automatix, else just take your chnces, you dont have to remove anything.
5. This may get configured for you, im not sure.

Thanks. I will try your suggestions and attempt an upgrade...

:)

---

### Post by c_martini on 2007-10-18
Hmmm not good.. After several hours, the upgrade stops at 52% with an error something about it not able to install some ttf deb package (suspect its a font package of some kind). The upgrade just hangs there at 52%. I am afraid to close out of the upgrade wizard as I don't want to leave the system in an unusable state...

:confused:

---

### Post by c_martini on 2007-10-18
I have now recovered this failed setup by first killing the upgrade processes and then doing:

```

sudo dpkg --configure -a
sudo apt-get autoremove

```

This seems to have worked although there are a coupldf of small things broken, such as Compiz...

---

