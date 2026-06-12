---
title: "Blank screen when booting live USB"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by steever on 2011-04-28
Hi.

I have an emachines 525 notebook (I know, I know :rolleyes:).  When I try to boot the Natty live USB, I get a blank screen.  I can boot it with nomodeset, but the resolution is wrong.  Maverick and Lucid both worked perfectly out of the box with this machine.

Any ideas?  I am hesitant to install, but so looking forward to it.

Thanks in advance.

---

### Post by wilee-nilee on 2011-04-28
> **steever said:**
> Hi.

I have an emachines 525 notebook (I know, I know :rolleyes:).  When I try to boot the Natty live USB, I get a blank screen.  I can boot it with nomodeset, but the resolution is wrong.  Maverick and Lucid both worked perfectly out of the box with this machine.

Any ideas?  I am hesitant to install, but so looking forward to it.

Thanks in advance.

You will need a graphics driver, that is why you're using nomodeset to be in an low graphics mode. You will have to add that to the kernel line after install to get in and install a driver. Run this in a Ubuntu terminal to identify the card.
lspci | grep VGA

When you add it (nomodeset) to the grub menu at boot it is only a per session change. To get the grub menu to show if your not dual booting, hold down the shift immediately after powering on. Hit e at the grub menu insert nomodeset after the word splash at the end of the first kernel line, hit crtl-x to boot to a command line I think login and then type startx to start the desktop. You would then look for the driver starting in the menu-system-additional drivers. This is all from the install not the cd live.

You can post the card and hope for an answer but I would just look on Google with the card and Ubuntu,for the quickest links and answers, post the card though.

Chances are that you will be fine though.

---

### Post by reauxbeauxboy on 2011-06-27
*You will need a graphics driver, that is why you're using nomodeset to be in an low graphics mode. You will have to add that to the kernel line after install to get in and install a driver. Run this in a Ubuntu terminal to identify the card.*

I'm having the same issue here (same laptop too... I know, I know -- but they were cheap at WalMart!) I've done the lspci | grep VGA and gotten this result:

00:02.0 **[COLOR="Red"]VGA[/COLOR]** compatible controller: Intel Corporation Mobile 4 Series Chipset Int
egrated Graphics Controller (rev 09) 

Can anybody tell me what do I do to get and install a good driver there?

Thanks!

-Rob

---

