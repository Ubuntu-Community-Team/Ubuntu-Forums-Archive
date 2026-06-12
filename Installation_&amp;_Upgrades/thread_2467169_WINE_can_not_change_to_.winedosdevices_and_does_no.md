---
title: "WINE can not change to .wine/dosdevices and does not open"
date: 2021-09-17
forum: Installation &amp; Upgrades
---

### Post by Roland_Msl on 2021-09-17
Had already installed WINE on Ubuntu 16.04 and on 20.04.1
Last weak crashed my SSD and I installed 20.04.3 on the new SSD. 

My most important Windows Programs are POV-Ray and HP 41 emulator.

Both bring a small window with an error message

Failed to launch "POV-Ray"
Failed to change to directory "/home/founder/.wine/dosdevic...

But preinstalled programs work, in terminal
wine explorer
opens the explorer.

I already removed .WINE, deleted the folder .wine and reinstalled version 6.0.1.

---

### Post by MAFoElffen on 2021-09-19
Seems like it was trying to change directories to something that was no longer there or no longer exists (more rather: existed).

The obvious question would be if /home/founder/.wine/dosdevic exists... But you already said you deleted everything under $HOME/.wine, so it's already to late (and pointless) to ask to do a directory list of that address... or anything under ~/.wine, because you deleted the whole directory tree. Right?

---

### Post by grahammechanical on 2021-09-20
I would ask: Did you re-install Wine and then use Wine to re-install these two Windows programs? I know the answer is obvious but if we copy the Wine configuration files from one SSD to another SSD it may well be the cause of this issue. I am not familiar with either of these Windows programs but for them to need to access .wine/dosdevices/ they must need to access some part of the hardware.

I am wondering if /home/founder exists on this new installation. Has another username been given and old configuration files used?

Regards

---

### Post by monkeybrain20122 on 2021-09-21
BTW povray has a linux version and it is in the repo.

---

