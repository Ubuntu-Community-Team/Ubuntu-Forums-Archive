---
title: "Upgrading Ubuntu 10.10"
date: 2013-08-14
forum: Installation &amp; Upgrades
---

### Post by jason12 on 2013-08-14
I have Ubuntu 10.10 installed and I want to upgrade to the latest LTS version. In Update Manager it says:

 
**New Ubuntu release 11.04 is available**
 
but if I click upgrade I get the error message:
 

 [B]Failed to fetch
 Fetching the upgrade failed. There may be a network problem.  [/B]
 

 (The network is fine. I can access external web pages).
 

 Now System->About Ubuntu says I'm running 11.04 but lsb_release -a says I'm still running 10.10
 How can I get upgraded to the latest LTS version of Ubuntu?

---

### Post by SweetAurora on 2013-08-14
You unfortunately missed the upgrade ship a long, long, time ago. You have no other options except reinstalling with Ubuntu 12.04 or newer. Canonical only gives a limited window to upgrade and if you don't, tough break.

---

### Post by arpanaut on 2013-08-14
It is still possible:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

But you are probably better off backing up and doing a fresh install.

---

### Post by SweetAurora on 2013-08-14
@arpanaut.

No he can't. the Maverick repos have been removed from the archives. His system cannot update it's packages anymore. Also Natty is gone too.... So he couldn't even update to that if he wanted.

Don't believe me? Look at the archives yourself. [http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/)

---

### Post by arpanaut on 2013-08-14
Did you read the link I provided?
It is possible using the "old-releases" repositories, but as I said it would be easier to do a fresh install.
It would take multiple upgrades, and edits to the sources,list but it is possible, though not advised.

P.S. I know bec. I tried it once to test and it worked but is a pain in the you know what,
hence my advise to do a fresh install.

---

### Post by SweetAurora on 2013-08-14
Didn't even know that repository existed! I've only seen people here talk about the Archives PPA. Sorry about that. :redface:

---

### Post by deadflowr on 2013-08-14
Though switching over the repos to the old release repos and upgrading that a way will work.
It would be better and quicker to just back up you data, download a newer version, and do a reinstall.
There is a lot of rinse and repeat trying to upgrade from maverick to precise.

Added: One of the things the Ubuntu technical board discussed when deciding to switch over to a shorter support cycle(9 months from 18 months) was to see about allowing any release be upgradable to LTS.
As of now only LTS to LTS and releases directly before them could(can)

[http://fridge.ubuntu.com/2013/03/19/changes-in-ubuntu-releases-decided-by-the-ubuntu-technical-board/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+ubuntu-news+%28Ubuntu+News%29](http://fridge.ubuntu.com/2013/03/19/changes-in-ubuntu-releases-decided-by-the-ubuntu-technical-board/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+ubuntu-news+%28Ubuntu+News%29)

---

### Post by jason12 on 2013-08-21
Is there a way to install a new version of Ubuntu over my old 10.10 so that I keep my file system, data, installed apps and configurations intact?

---

### Post by Frogs Hair on 2013-08-21
A new version of Ubuntu would overwrite the old. There is a possibility of moving home to a partition. Any non-default applications that are still supported have been updated for Gnome 3 so configurations for them may not be applicable.

 Depending how much data you have moving home may be worth while and profiles for applications stored home/hidden would be preserved. I have no experience using a home partition and you may want to start a new thread regarding the use of a home partition. I find backup to be to a better method based on how much data I keep on Ubuntu.

If something were to go wrong while moving home if you decided to go that route it would be best have physical backup anyway.   [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

