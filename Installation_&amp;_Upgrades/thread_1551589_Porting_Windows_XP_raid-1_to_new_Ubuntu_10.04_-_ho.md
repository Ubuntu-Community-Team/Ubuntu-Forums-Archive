---
title: "Porting Windows XP raid-1 to new Ubuntu 10.04 - how?"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by JensLH on 2010-08-12
I have recently bought a new computer, and would like to take my existing RAID-1 from the old computer to the new computer, as the disks hold many digital photos. The old RAID-1 was in a DELL XPS 400 (and based on the intel 82801GR chip I guess), and the new computer has an intel ICH10R. I understand that both chips require a Windows driver if RAID-1 is needed.

The old disks still reside in the "dead" computer. How can I proceed? I hope the solution is that fakeRAID can be enabled, but I would like to ask the clever and experienced community before I do something that cannot be undone (and maybe lose all my digital photos!). Or maybe you have a better solution?

If you need more information to help me then please tell me to post information; I do not really know much about setting up RAID-1.

---

### Post by ronparent on 2010-08-12
I have done it moving a raid 0 from one nvidia based controller to another while retaining all of the data. When I moved the same raid0 disks from a nvidia based MB to an AMD based system, all partition tables were lost and the disk's data essentially loss. Also you can't go back once the move is made. So I would not advise you trying (unless everything were backed up).

In your case, since you have a raid 1, you might be able to move only one drive of the set and access it in a non raid environment. That has its own unpredictable pitfalls. It may be accessible to read and backup all your data, BUT, dmraid should be uninstalled before you try it. Tread carefully because the wrong move could destroy your data.

---

