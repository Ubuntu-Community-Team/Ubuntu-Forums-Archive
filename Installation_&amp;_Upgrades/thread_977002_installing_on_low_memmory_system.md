---
title: "installing on low memmory system"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by jklslvch on 2008-11-09
Im downloading Ubuntu 8.10 alternate CD... From what im reading in this page [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) is that it installs a base system and lets you choose whatever else to install... And from what else iv been reading about Ubuntu 8.10 is that with its Xorg upgrade Nvidia legacy (TNT models) drivers dont work with it... 

So my question is: Can I install the base and everything but instead of installing the latest Xorg I install the version before the latest to be able to use the original drivers and install the rest the same?

Computer:
Pentium 3 (597MHz)
384 RAM

---

### Post by Rocket2DMn on 2008-11-09
It's not generally recommended to do a regular install then change the version of a core package like X, it is too likely to create problems within the system.  You might just consider using Hardy since it is a LTS release, and so is supported on the desktop for 3 years.  Trying to force Hardy's X in Intrepid could very easily create complications.

---

### Post by jklslvch on 2008-11-09
> **Rocket2DMn said:**
> It's not generally recommended to do a regular install then change the version of a core package like X, it is too likely to create problems within the system.  You might just consider using Hardy since it is a LTS release, and so is supported on the desktop for 3 years.  Trying to force Hardy's X in Intrepid could very easily create complications.

yeah... did you look at the link.. i thought it was like an arch linux install because it has a part where it says "Installing X.org" thats where my question arises i dont want to install the latest verion of Xorg i want the previous version...

from what i see that it is is a base system install command line only and from there on you add what you want... one of the things i was wantig was the older Xorg.. but iv never used ubuntu in this way and dont know how to install specific verions of packages like in gentoo

---

### Post by Rocket2DMn on 2008-11-09
Though I haven't installed Arch (it's on my to-do list), the Ubuntu installation process is not as customized as with Arch and Gentoo.  When versions are released, they go through a development cycle and are settled on specific versions of core packages which remain unchanged through the version's support life (SRU's - stable release updates excepted, like for security fixes).  I believe Arch is a rolling distribution which tends to always keep the latest versions of packages.  In Gentoo you compile the software yourself, which makes it easier to use other versions.  Ubuntu installation does not provide you the option to install different versions of packages, and I don't recall if using the Alternate Install CD gives such detailed options as selecting specific software.  A [Minimal Install]("https://help.ubuntu.com/community/Installation/MinimalCD") would give more detailed options, but still wouldn't provide different versions.

I don't believe Ubuntu keeps alternate versions of core software in the repositories for a specific release, so if you wanted to use Hardy's X, you would need to do your installation and updates, then set the Hardy repositories in your sources.list (or in System->Administration->Software Sources) and Force Version through Synaptic.  Alternative to forcing version is uninstalling X and re-installing the version in Hardy's repos after disabling Intrepid's repos.  Then when you are finished, you would need to disable the Hardy repos and re-enable the Intrepid repos.  This alone is a touchy and somewhat dangerous process, with no guarantee of success even when performed correctly.

---

### Post by jklslvch on 2008-11-09
Hmmm... I understand now

Well do you think anytime soon Nvidia drivers will be supported?

---

### Post by Rocket2DMn on 2008-11-09
I have no idea what the story is with nvidia legacy drivers.  I've heard people suggest (kindly) emailing nvidia and requesting that they release drivers compatible with the new kernel and version of X.  There was a lot of pain with restricted drivers during Intrepid's development cycle, so I don't know how long it will be before drivers are available.  Sorry.

---

### Post by jklslvch on 2008-11-09
Well since you know more about the package manager...

Can I install 8.04 and update Gnome without having problems?

---

### Post by Rocket2DMn on 2008-11-09
Again with the core package versions, it is possible to have problems.  If I had to compare the two options though, I would think that installing the Intrepid Gnome on the Hardy X is more likely to succeed than the other way around (upgrading a core package seems more feasible than downgrading a core package).  This means you would do a Hardy install, then enable the Intrepid repo, upgrade ONLY Gnome and then disable the Intrepid repo before every doing anything else with the package manager.  I don't have a step by step process on this, though.  If you choose to take this path, you should look around to see if others have tried and to check out if they have been successful, or what problems they have run in to.

If you want me to try and walk you through it, I can try and look up some more details (like the specific packages and dependencies), but it will take time; I'm actually going to bed right now.  I will check up on you tomorrow evening, let me know what you decide (if anything).

---

### Post by jklslvch on 2008-11-09
Well im goint to download 8.04 Alternate and try to update some thing and see how it goes..

---

