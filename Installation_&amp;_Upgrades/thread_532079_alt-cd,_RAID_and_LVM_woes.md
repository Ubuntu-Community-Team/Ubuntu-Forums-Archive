---
title: "alt-cd, RAID and LVM woes"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by raijinsetsu on 2007-08-22
Are there plans to improve RAID and LVM support in future installs? As it stands now, it takes forever to do a RAID/LVM install.

Raid is not so much a problem, except that if you try to set up the raid, and then decide that you made a mistake, OR, you attempt to change a previous raid configuration, you get a message to the affect that the kernel doesn't know about your partitions anymore, and you HAVE to restart to do your changes.
Also, dmraid is not available on any install that I can find, and there's no support for installing/using additional packages needed for installation on the alt-install CD(none that I can find at least)

LVM is a total pain. That LVM timeout bug really needs to get fixed. When I set up my VG, I have usr, local, home, and sometime opt and var. At 5-10 minutes for the timeout, EACH, that's almost an hour, just for partitioning. And that's if you didn't make any mistakes.

Are there plans to fix any of these issues?

---

