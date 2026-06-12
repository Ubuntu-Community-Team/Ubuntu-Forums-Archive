---
title: "Upgrade to 7.10 and install XP"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by elijahbenraam on 2008-01-21
Hi, I really need some advice on this, so any thoughts will be appreciated.

I have 7.04 installed on my computer and I've just got two disks as a gift - one with Ubuntu 7.10 and another with Windows XP SP2. 

I want to upgrade to 7.10 using the disk (not internet), but I'm not sure what and how to back up. I know that I should just back up my whole home folder but what about all the programs that I've installed and upgraded over the last year (I really don't want to download it again - internet is not cheap here). 

At the same time I want to install Windows so I can play some games and use some programs that I have for Windows. I don't have a special partition for Windows. 

What would be easier - back everything up and start from scratch or try to upgrade to 7.10 and then somehow create a partition for windows? The first option seems easier to me but I'm worried about all the programs and updates to them - will I be able to get it all back without reinstalling them?

Thanks a lot.

---

### Post by zvacet on 2008-01-21
You can upgrade only from alternate CD,so you can do it if your Cd is that one.If it is live you can not do upgrade with it.Try [this](http://www.psychocats.net/ubuntu/partimage) for backup.You can make space for Windows with [Gparted](http://gparted.sourceforge.net/).

---

### Post by elijahbenraam on 2008-01-21
Thanks, zvacet

How do i get the alternate CD? I just downloaded the cd from the main site and not sure if it's live or alternate?!

If I use partImage after I install 7.10 will it restore just the programs or will it overwrite the new installation?

---

### Post by PmDematagoda on 2008-01-21
You can download the Alternate CD from [here]("http://releases.ubuntu.com/7.10/").

---

### Post by elijahbenraam on 2008-01-21
Thanks, but is it at all possible to back up my programs? Even for the future - if something happens and I have to reinstall the system I will need to reinstall all the programs and I don't want to download them again. 

When I install something through Synaptic or Add/Remove Applications - is the package saved somewhere or is it deleted after the download and intallation?

---

### Post by zvacet on 2008-01-21
You can find them in **var/cache/apt/archives**

---

