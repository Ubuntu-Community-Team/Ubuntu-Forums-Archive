---
title: "Requested Backup/Install Information"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Precipitous on 2009-10-02
I am currently running Ubuntu Studio Jaunty. The way I have it installed is the root files are on my boot drive, and the Home directory, data, etc. is on a secondary one. What would be the best backup/install strategy, should I decide to install Karmic from scratch, as opposed to doing an upgrade?

Thanks in advance for your assistance.

---

### Post by slakkie on 2009-10-02
Use clonezilla to make a backup of your root partition. Then you can upgrade via update-manager or do-release-upgrade. Or you upgrade via the alternate CD or freshly install the beta via a Live CD. 

IMO, it doesn't matter how you want to upgrade, as long as you backup your / partition since you can recover to a working OS if things don't go well.

---

