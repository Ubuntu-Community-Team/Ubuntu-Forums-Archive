---
title: "raid 0 motherboard swap"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by kezeb on 2010-09-10
hey i just got a new motherboard for a router/server at home i got something beefier, the deal is that the raid 0 i've got running on the old chipset is running ubuntu desktop edition and i just wanna install the server edition on the new beefier board, i've a /home partition in the raid if i swap the boards will that crap out what i've got in my /home dir... or can i just swap the boards and make a fresh install on a root partition without messing up my /home partition?

---

### Post by ronparent on 2010-09-10
Is it a software raid or fakeraid? If a fakeraid it may not be transferable unless the new MB uses the identical raid chipset. I have, for instance, successfully moved a raid 0 from on MB to another with the identical chip set. The same type move to a MB with a different manufactures chipset resulted in wipe of the partition tables (expected and planned on). In any case you would be advised to have everything you want to be backed up.

The home will probably work with a new install regardless of what transpires in the transfer even if it has to be restored from backup. You do want it in place so it is present for duty if a new install is made. Glitches are possible but fixable. Just be sure to check the the /home is not marked for formatting.

---

### Post by kezeb on 2010-09-10
well it turns out it's a fake raid so i've gotta backup everything before installing the server edition, though i'm not certain where to put my bak up it's about 2TB's.
thanks for the help!!!!!!!!!

---

