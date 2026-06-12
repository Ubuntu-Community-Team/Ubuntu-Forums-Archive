---
title: "wifi problem upgrading from fesity to gutsy"
date: 2007-10-06
forum: Installation &amp; Upgrades
---

### Post by jlmath on 2007-10-06
Yesterday I upgraded my Linux desktop from Feisty to the new Gutsy beta. The upgrade went flawlessly (as usual) with one nasty exception.  My system uses a Linksys PCI wireless network adapter. On a previous upgrade (I believe from Dapper to Edgy) I had to mess with drivers. However the upgrade to Feisty handled it with no problem. Unfortunately Gutsy appears to have a catch-22 in the upgrade. In order to get on the internet, my wireless card must work. In order for my wireless card to work, the HAL Atheros driver must be operational. This requires the restricted driver manager. The upgrade doesn't install this. Therefore it has to be downloaded. However in order to download it my wifi adapter needs to have it installed.

I do have the Feisty DVD that came with the Official Ubuntu Book. I booted from it and lo, it has the restricted driver manager and it works. So, does anyone have any suggestions as to how I can get around this problem?

Although I'm reasonably competent, I know just enough to be dangerous to my installation.

Another note, the package manager for gutsy shows that restricted-manager 0.33.1 is installed. However when I attempt to execute the restricted manager I get a warning message that states:

You need to install linux-restricted-modules-2.6.22-13-generic for this program to work. 

This however must be downloaded and I can't access the internet. Is there any way I can get this to my file system either downloading to my windows system and burning a cd, or from my Feisty DVD? At the moment my Gutsy system has no "web" feet.

Thanks for your assistance::confused:

---

### Post by jlmath on 2007-10-06
:) Problem is fixed!! Although I received no replies, I did see another message from sixfoottallrabbit regarding the same Linux module. One response to his problem by Creatorlarry provided the answer. I rebooted using Escape to boot a previous kernel version which had an earlier version of the same module. This brought my network adapter back to life and I was able to download all upgrades including the missing Linux-Restricted module. Rebooted and all is well.

---

