---
title: "Problem updating jkakavas-creepy-lucid"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by DavidInGA on 2011-04-07
I am new to Ubuntu.  I've been running it for a few months, but I don't yet really understand the upgrade process.  When I run the Update Manager, I get the following error:

> 
Failed to fetch [http://ppa.launchpad.net/jkakavas/creepy/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/jkakavas/creepy/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.


Sure enough, this file doesn't exist.  I found the reference to it in /etc/apt/sources.list.d/jkakavas-creepy-lucid.list:

> % cat jkakavas-creepy-lucid.list
deb [http://ppa.launchpad.net/jkakavas/creepy/ubuntu](http://ppa.launchpad.net/jkakavas/creepy/ubuntu) lucid main


Is there some other value I can set there that will allow me to get the upgrades and fixes that I need?  I have no objection to upgrading to a new version if that's what I need to do, but I'm not clear how to fix this error and proceed. 

Thanks!

---

