---
title: "FireFox Upgrade 0.9.3 - 1.0.2"
date: 2005-04-05
forum: Installation &amp; Upgrades
---

### Post by chicom on 2005-04-05
Hi, I've just installed Ubuntu 4.10 and looking through the Synaptic Package Manager I see  the Package Manager does not show version 1.0.2. I've downloaded version 1.0.2 and followed the install intructions and Version 1.0.2 loads once the install completes. Problem is I cannot get the newer version to run from there on. I'm also looking for ways to import my bookmarks etc.

Thanks,
Chico :?:

---

### Post by shakin on 2005-04-05
[QUOTE=chicom]Hi, I've just installed Ubuntu 4.10 and looking through the Synaptic Package Manager I see  the Package Manager does not show version 1.0.2. I've downloaded version 1.0.2 and followed the install intructions and Version 1.0.2 loads once the install completes. Problem is I cannot get the newer version to run from there on. I'm also looking for ways to import my bookmarks etc.

Thanks,
Chico :?:[/QUOTE]

You need to add the warty-backports repository to /etc/apt/sources.list (or using the Synaptic repositories editor). Add this:

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-backports main universe multiverse restricted 

Then you will be able to upgrade Firefox using Synaptic.

However, you might want to search the forum for how to upgrade to Hoary and you'll get 1.02 when you upgrade. There are enough enhancements in Hoary that it's worth the upgrade, and it's very stable.

---

