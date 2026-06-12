---
title: "It should be possible to use the live cd to help in upgrades"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by bradtem on 2007-12-20
As not everybody knows, the alternate install CD offers an offline upgrade tool, which is fine.  The live CD, however, does not, presumably for space reasons.

However, I find myself often downloading the live cd for new releases anyway.  Either because I have a new system I am going to convert to ubuntu, or I want to do a wipe install, or most probably because I want to try the new release on my hardware to make sure all is well before committing to an upgrade.   (That's wise, I found that gutsy's driver for my marvell ethernet is broken where feisty's was fine, and so I temporarily put a pci ether card in the box before the install.)

However, it seems a shame that when I am ready to upgrade using the update-manager or similar that it makes no use of the lovely live-cd full of debs that I have.   If apt-get and the updater had a way to detect (or be told about) the presence of the CD, and then to check to see if any packages they wish to download can be found on the CD before downloading them, this would make the upgrade run faster for me, and reduce the load on the respository servers.   Ideally this could be automatic -- look for a mounted CD and check its signature for a repository of debs, and treat them as cache.

It might even be possible to do an offline upgrade this way, but I'm not expecting it.  I expect it to go to the net to check for any new versions and security updates etc. since the CD was finalized anyway.   And of course the packages I have which were never on the CD will have to be upgraded from the net.

Is this something you can do already? I've never seen any statement about it.  If not, I think it's a worthwhile idea.

---

