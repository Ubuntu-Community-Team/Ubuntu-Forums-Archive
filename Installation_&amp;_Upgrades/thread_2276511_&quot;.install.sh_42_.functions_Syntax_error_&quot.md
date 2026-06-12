---
title: "&quot;./install.sh 42: ./functions: Syntax error: &quot;(&quot; unexpected&quot; I can't install driver"
date: 2015-05-03
forum: Installation &amp; Upgrades
---

### Post by SecretSociety68 on 2015-05-03
Hi, 

I'm new to Linux. I've been playing around with it since March 2015 (I've learned allot so far, but not enough yet ;))

I'm having networking trouble =(



I have Ubuntu Desktop v15.04   x64 installed. I'm in Unity mode, not KDE or GNOME. I just freshly installed it on my Desktop PC. No other operating systems are on it, just Ubuntu. Despite networking trouble, Ubuntu seems to be running fine. I'm on my laptop right now to access the net to post this message. My desktop PC has a Netgear WG311v3 Wireless 802.11 b/g wirless card pci addon. And a Marvell Yukon 88E8001 pci gigabit ethernet controller(built into the motherboard). Right now, I can't get neither card to work to gain internet access. At first, I ignored the ethernet and tried to set up my wireless card, I did this in Ubuntu: (you can just call me newbie! ;))

1. Clicked on the gear icon on the left panel for "System Settings"
2. Clicked on the "Software & Updates"
3. And then clicked the "Additional Drivers" tab.

But it only says "No additional drivers available"

At that point, since I didn't find any additional drivers, I decided to just plug my router (an Xfinity TG826G router) directly into the 88E8001 ethernet nic. And as soon as I did, Ubuntu locked up instantly. The mouse would not move, so I pressed the reset button to reboot. Ubuntu started to boot, and then it froze again before it even made it to the logon screen. I realized by having my router plugged in, Ubuntu would not work. After I unplugged it, Ubuntu worked fine again. I can use the router with my laptops ethernet without such a problem. Not that it matters, but the laptop is running Windows 8.1, in case if you were wondering if I had Linux on this laptop, I do in Virtualbox, and it runs fine. So I went to Marvell Yukon and downloaded there Linux driver for the 88E8001 ethernet card to install them on the Desktop PC in Ubuntu before I even attempt to plug the router back into the 88E8001 ethernet card. Then I ran into an installation errror with the drivers. (I read the instructions from the driver readme to the "T")

I type this in a terminal window:

```

sudo su (then enter my password and that makes me root user #)

./install.sh  

( or I type it this way)

sh install.sh


```


I get this error message:

```

  ./install.sh 42: ./functions: Syntax error: "(" unexpected

```

I'm not totally sure why Ubuntu locks up as soon as I plug the router into the Desktop PC, I don't know if its a hardware compatibility problem with the 88E8001 ethernet card and the router. Thats why I wanted to install the ethernet drivers, and then try to plug it in again, because maybe it just needs the drivers first. My Netgear Wireless card manufacturer doesn't supply a Linux driver, only Windows drivers, so no luck there. The latest driver I just got for the 88E8001 ethernet card (from the manufacturer's site Marvell) was last updated 8-22-12 and it says for Linux Kernal 2.6.x

Its the only Linux driver version they have listed at their site, or I would have tried other versions. Is something wrong with the "install.sh" file? 

Thanks for any help!

---

### Post by dino99 on 2015-05-03
The kernel is already aware of the required driver (skge) for that 88E8001 chipset:

> config SKGE
	tristate "Marvell Yukon Gigabit Ethernet support"
	depends on PCI
	select CRC32
	---help---
	  This driver support the Marvell Yukon or SysKonnect SK-98xx/SK-95xx
	  and related Gigabit Ethernet adapters. It is a new smaller driver
	  with better performance and more complete ethtool support.

	  It does not support the link failover and network management
	  features that "portable" vendor supplied sk98lin driver does.

	  This driver supports adapters based on the original Yukon chipset:
	  Marvell 88E8001, Belkin F5D5005, CNet GigaCard, DLink DGE-530T,
	  Linksys EG1032/EG1064, 3Com 3C940/3C940B, SysKonnect SK-9871/9872.

So its ready to work 'out of the box' without needing tweaks. About the router it might be only a bad setting(s) problem within it.
From a terminal you can run > sudo journalctl to get details about warnings/errors (red lines highlighted)

---

