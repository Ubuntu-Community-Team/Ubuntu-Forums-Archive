---
title: "Video card driver &amp; backup"
date: 2010-08-31
forum: Installation &amp; Upgrades
---

### Post by zslevi on 2010-08-31
6 months ago I downloaded the freshest Ubuntu (9.10) and tried to install ATI drivers. The ATI drivers didn't really work out, the screen  gone blank at booting, and I couln't fix the problem by removing the ATI package from command line. So I reinstalled the whole system, and gone with the standard opensource VESA driver. Later I read, that the problem might have been with the new Xorg version, and was recommended going with 8.04 LTS (it has the older Xorg version). Since then I did a partial upgrade (I now have the 2.6.31-22 kernel version), but still has the 9.10 Karmic, and the default video driver.  I'd like to give the latest ATI driver a try, maybe upgrading to 10.04 as well, but I don't know how to do it safely. I'd prefer not to make an image of the whole partition, as it grew quite big by now (22 GB). I thought having a copy of /etc/conf and /boot might do it. What do you think?
How would you do this upgrade and backup?

P.S.:
The data in this partition isn't particularly valuable, but I spent quite a bit of time with configureing it. So I would be contempt with a solution that exports all the installed package information and conf files , to quickly reinstall if things go wrong. (I guess kickstart could do it, but I'm not very familar with it, and don't know how well it's supported in ubuntu)

---

### Post by Mark Phelps on 2010-08-31
The fact that the ATI drivers failed the first time implies that you have one of the older legacy cards that does not have current drivers.

What make/model is your card? Unless it is one of the newer HD 3x/4x/5x cards, there are no current ATI drivers that will work with it and trying to force their installation is only going to trash your display.

With the legacy cards, the open-source driver is installed by default and that is the ONLY driver that will work with Ubuntu versions newer than 8.10.

---

### Post by coffeecat on 2010-08-31
With my - admittedly fairly recent - HD4200 card, the open source ATI driver worked, but didn't give me 3d acceleration in Karmic, 9.10. But now I can get compiz enabled with the OS driver in Lucid and in Maverick Alpha. Trying to install the proprietary fglrx driver merely resulted in blood, toil, sweat and tears.

This doesn't help you if your card is a legacy card, but I point this out because the ATI driver seems to be getting better and it might be worth while trying the Lucid live CD to see if it copes. Failing that, is this a desktop machine? Have you thought of replacing the card with a newer one, possibly even a nvidia card?

---

### Post by zslevi on 2010-08-31
> **Mark Phelps said:**
> The fact that the ATI drivers failed the first time implies that you have one of the older legacy cards that does not have current drivers.

What make/model is your card? Unless it is one of the newer HD 3x/4x/5x cards, there are no current ATI drivers that will work with it and trying to force their installation is only going to trash your display.

With the legacy cards, the open-source driver is installed by default and that is the ONLY driver that will work with Ubuntu versions newer than 8.10.
It's not legacy card, it's a Radeon HD 3800 (now I'm logged in Windows, so I could check it more easily).

---

