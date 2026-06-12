---
title: "Upgrading from 6.06LTS Dapper to latest."
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by dmedici on 2007-06-27
Greetings! 

I would like to upgrade from 6.06LTS (Dapper) to the latest version (7.x) and have read through many of the posts here but am not understanding a few things. 
Is there a way to simply upgrade from the command line or do I have to use a series of previously installed programs to do this? 
If possible, I'd like to avoid having to burn a new cd and start all over again. 
I'm fairly new to this and would really like to move all my machines to Linux as Windows is killing me over here with constant trojans, spyware, virii and broken M$ updates. Any help would be appreciated.

---

### Post by avtolle on 2007-06-27
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes) may be of some assistance. If you don't want to burn a CD and do a fresh install, the progressive upgrade path is one way to do it, e.g., a "dist upgrade" from 6.06 to 6.10, followed by a "dist upgrade" from 6.10 to 7.04. This would be very time consuming.

---

### Post by haden9 on 2007-06-27
The easiest way is to use the Software Update manager, but first open a terminal and type in:

sudo gksu “update-manager -c ”

This will prompt for all updates, then exit out of the and head into System-->Administration-->Software Updates

You should see 6.10 available for upgrade (we will get to 7.04 eventually after this upgrade is complete) now click on the buttom to upgrade and continue till it actually is applying the upgrade, when its done just reboot.

Again for 7.04 use the:

sudo gksu "update-manager -c"

Head back over to Software Updates in System-->Administration-->Software Updates, it should show up now 7.04, upgrade and reboot and that should do it!!!

Hope this works out for you! Good luck!

:popcorn:

---

### Post by dmedici on 2007-06-28
Many thanks for your quick reply as the upgrade worked flawlessly. I really appreciate you taking the time and effort to answer my question.  :D

---

