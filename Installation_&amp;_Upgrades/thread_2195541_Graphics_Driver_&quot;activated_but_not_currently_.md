---
title: "Graphics Driver &quot;activated but not currently in use&quot;?"
date: 2013-12-24
forum: Installation &amp; Upgrades
---

### Post by bigtinyman on 2013-12-24
Hi all,

I'm pretty new to Linux. I've installed WINE, hoping to play Starcraft 2 with it. Problem is, when I run the game, the framerate is extremely low, making for a super laggy game. I know my system has the specs to run it, since the game is flawless on my Windows OS. I think it might have something to do with my graphics card drivers. I've downloaded the proprietary driver for my AMD Radeon card from the Additional Drivers application, but I get an issue that many others seem to have. It says "This driver is activated but not currently in use." I searched around on the internet, and there's no clear answer as to how to use the driver.


So how do I set the driver to be "in use"? Also, is there anything else that might be making the game laggy?

I'm running Ubuntu 12.04

---

### Post by grahammechanical on 2013-12-24
Did you install the proprietary video driver through the Additional Drivers utility? Proprietary video drivers usually have a settings manager that is installed the same time as the driver. You should find this in the Dash>Applications>Installed. That settings manager will confirm or otherwise the use of the proprietary driver.

What rating does winehq give to that game? The wine developers try their best but they cannot work miracles. They do not claim to do that. This lists Starcraft II as Platinum

[http://appdb.winehq.org/](http://appdb.winehq.org/)

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882)

[https://wiki.archlinux.org/index.php/StarCraft_2](https://wiki.archlinux.org/index.php/StarCraft_2)

You might need the latest version of Ubuntu and the latest version of wine. I do not know about these things. What version of Windows are you running this on?

Regards.

---

### Post by bigtinyman on 2013-12-25
I have an AMD Radeon HD graphics card, and yes, I have the AMD Catalyst Center installed which is the manager for the driver. But the game is still laggy. Any other things I could try?

---

### Post by Mark Phelps on 2013-12-25
> I have an AMD Radeon HD graphics card,

Not enough info, as the older Radeon HD cards were dropped from Linux proprietary support by AMD last summer.

What MODEL Radeon card is it?

---

### Post by bigtinyman on 2014-01-07
Radeon HD 7850.

How can I check to see if the card is still supported? As far as I can tell, it should still be supported.

---

### Post by QIII on 2014-01-07
Is this a desktop or a laptop?  If the latter, does it have hybrid Intel/ATI graphics?

---

### Post by bigtinyman on 2014-01-07
> **QIII said:**
> Is this a desktop or a laptop?  If the latter, does it have hybrid Intel/ATI graphics?

It is a desktop card.

---

