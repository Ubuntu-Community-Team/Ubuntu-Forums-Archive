---
title: "Test upgrade in virtual machine?"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Asmodai on 2010-04-30
I'd like to upgrade to 10.04 from Karmic but want to make sure it will leave me with a working system afterwards.
I figured a good way to test it is to create a disk image with dd and then try upgrading in VirtualBox using that image. The idea is that if it is successful, it'll probably be successful on the real machine too.

The only problem is my home partition, which is >1.4 TB. I don't have that much space left on any other hard disks. So I would like to somehow exclude certain directories in /home (or the entire partition) from appearing in the image.

Is this even possible? Or does anyone have any better ideas?

---

### Post by P4man on 2010-04-30
it will not test the things that are most likely to fail, like hardware drivers. Sounds like a waste of time to tbh.

Why not just backup your / partition, do the upgrade, and should it not work, restore from backup. If you want to be sure no changes are made to your /home, then just dont mount it, let it create a /home in your root partition. Once everything works, add your "old" user and mount your /home.

---

### Post by Asmodai on 2010-04-30
Thanks for the suggestion. Creating a backup of / is probably the best solution.
I'm just somewhat afraid that other partitions might get messed up even if they're not mounted - but I suppose these concerns are mostly baseless.

---

### Post by P4man on 2010-04-30
actually I wasnt thinking quite straight as you cant just unmount /home or create a user with his home on a different partition (the latter is probably possible, but I dont know how). I was thinking of a fresh install, not an upgrade, then you could easily keep the /home partition unmounted and untouched.

---

### Post by Asmodai on 2010-04-30
Ah. I'd like to avoid a fresh install... it might take several days or more, considering I have many manually installed applications and libraries, some of them with custom patches applied.
Still, I would guess that the only changes that upgrading *should* do to the /home partition is updating configuration files and such, so I could backup those as well.

---

