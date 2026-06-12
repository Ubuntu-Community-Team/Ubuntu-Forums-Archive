---
title: "Upgrading from Gutsy...Frustrating"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by eeshking on 2007-11-23
Well, I've encountered a lot of problems upgrading from Feisty to Gutsy. First off, before I even upgraded, my wireless internet connection has been pretty bad ever since I got Feisty. I'm using a Netgear WG111v2 and it had out of the box support from the wireless network connection thing, but unfortunately, the connection kept crashing every once in a while. I tried using ndiswrapper but to no avail. Because of this, I was unable to download the update to get from Feisty to Gutsy--the internet connection would crash too frequently to successfully download it. So, I downloaded the Gutsy alternate install CD on another computer and burned it. I successfully used that to upgrade from Feisty to Gutsy, but when the upgrade finished and my computer restarted, the screen resolution was at 800x600. First, I tried to look at the screen resolution settings page to set it from to a higher resolution, but 800x600 was the only resolution there. Then, I thought the proprietary driver for the ATI Radeon graphics card might not be enabled, so i went on over to the restricted drivers manager, only to find out that it wouldn't start up after I entered the password. I tried running it from the command line, only to find an error message. Then I tried updating apt-get and reinstalling restricted-manager, but it did absolutely nothing. Furthermore, I can't even change my sources list from the GUI. So basically, I've got three problems: (1) Internet connection isn't great. If anyone knows how to make a WG111v2 work properly, I'd appreciate the knowledge. Right now, whenever the internet connection goes down, my preferred method of repair is to take out the network card from the USB port and stick it back in. (2) the resolution is stuck at 800x600, and it's possible that my proprietary drivers aren't working and (3) I can't change the sources list from GUI, nor can I access the restricted-manager

---

### Post by eeshking on 2007-11-23
Whoops,  I accidentally named this "Upgrading from Gutsy"...I meant to name is Upgrading from Feisty; I made another thread called "Upgrading from Feisty", but now this one's still here...could someone delete this?

---

