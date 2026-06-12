---
title: "What partition utility is used during initial installation of *buntu?"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by MurrayHewitt on 2010-12-11
I'm attempting to add an additional partition through KDE's Partition Manager, but my RAID 0 is not recognized by that program.

I'm wondering what partition utility is used during *buntu installation, as this properly recognized my RAID 0, and I was able to successfully manipulate the partitioning scheme.

---

### Post by ronparent on 2010-12-11
The answer to your question is gparted. But that sometimes doesn't see the raid either. The fix for gparted is to also install kpartx, That may work for KDE's Partition Manager as well? Post how you resolve it.

---

