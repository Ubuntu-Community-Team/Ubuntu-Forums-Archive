---
title: "Flash Plugin Download doesn't work"
date: 2010-11-08
forum: Installation &amp; Upgrades
---

### Post by cannotdrive on 2010-11-08
Hi-

I am running Ubuntu 8.1 with Firefok 3.0.3, with little to no updates since 2008.

I downloaded Adobe Flash Player .deb for Ubuntu 8, when prompted by a message on Hulu.com that said I needed to upgrade flash.  the link where i downloaded is here.: 
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

The plugin successfully downloaded but i still get the same message saying I don't have Flash.

?  Warning I am complete beginner.
Thank you

---

### Post by efflandt on 2010-11-08
In Firefox does Tools > Add-ons > Plugins show Shockwave Flash (what version)?  It is possible that you downloaded it, but did not install it.

It may be easiest to install it by going to System > Administration > Synaptic, click the circular arrow to refresh package lists.  Then when reindexing quick search finishes, type **flash** in Quick search, and look for **flashplugin-installer** (or **flashplugin-nonfree** if you do not find that).  Install that and see what version Shockwave Flash shows up in Firefox Add-ons.

---

