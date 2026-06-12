---
title: "Upgrade error"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by noelc on 2009-12-11
Hi Hope someone can help

When I attempt to upgrade my Ubuntu I get an error message saying

*The upgrade needs a total of 15.7M free space on disk '/boot'. Please free at least an additional 106k of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.*

I,ve tried the clean command in a terminal but nothung. MY hard drive has plenty of room?

Can some one help

---

### Post by lemming465 on 2009-12-12
Probably running **df -m** shows that /boot is a separate partition, and that it is using 185 MB out of 200 MB or something?  The way to fix that is to remove obsolete kernel packages.  One way to do that is to go to System->Administration-Synaptic Package Manager and search the *All* category for files whose names start "linux-image".  If you have more than 2, right click some of the older, lower numbered ones you aren't using, mark them for removal, and click *Apply*.  Getting rid of 2 or 3 obsolete ones should free up enough room.

---

