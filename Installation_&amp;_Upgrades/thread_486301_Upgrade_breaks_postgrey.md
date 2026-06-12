---
title: "Upgrade breaks postgrey"
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by TMC on 2007-06-27
I've just upgraded from Edgy to Feisty (using the 'distribution upgrade' button in the updates manager) and I now have a problem with postgrey.

Postgrey is now permanently shown as having an upgrade available from 1.25-1 to 1.27-4 but, when I try to upgrade, I get an error saying 

'E: /var/cache/apt/archives/postgrey_1.27-4_all.deb: subprocess new pre-removal script returned error exit status 1'

If I go into Synaptic to uninstall, I get the error 

'E: postgrey: subprocess pre-removal script returned error exit status 1'

I have tried deleting the .deb in the directory shown and stopping any and all services which might have anything to do with postgrey, no matter how remotely and I keep getting the same errors.

How can I resolve this problem?  I don't really care whether or not I end up with postgrey on my system, I just want my system to stop telling me that there's an update available.

Many thanks in advance,

David Shaw

---

