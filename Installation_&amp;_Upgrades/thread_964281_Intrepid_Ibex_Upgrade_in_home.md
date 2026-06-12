---
title: "Intrepid Ibex Upgrade in /home"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by xX-Felipao-Xx on 2008-10-30
Hi guys, my question is if its possible to make the upgrade, downloading the files the upgrade needs to download... in the /home directory, which in my case, its in another partition, which has enough free space.

And the partition with / mount point, has only 100mb of free space, and its all system, so I cant delete anything from there.

Any suggestion?

Thanks ;)

---

### Post by Partyboi2 on 2008-10-30
You would probably be better off using gparted live cd or a ubuntu live cd and decrease your  /home and increase your / partition as you will probably need to do this sometime in the near future as it won't take long to use that 100mb on updates etc.

---

### Post by xX-Felipao-Xx on 2008-10-30
Is this risky????

If not, I'll do it :), and after the upgrade is done, I'd like to delete what the upgrade downloaded..., because the free space in /home is not so much neither, 2 GBs, lets say I give 1GB more to /, and the upgrade stuff uses 700MB, there will be almost 500MB only free again.

Is this possible?

Thanks man ;)

---

### Post by Partyboi2 on 2008-10-30
I have never had a problem doing this but as always it is recommended that you always backup your important stuff before working on partitions.
Boot a [[COLOR=Blue]gparted live cd[/COLOR]]("http://gparted.sourceforge.net/") or a ubuntu live cd and open up gparted (System>Admin>Partition Editor) then unmount your paritions that you are resizing by right clicking on them and choosing to unmount. Then use the resize feature to shrink down your /home parition and then use the unallocated space to increase your / partition. This may take awhile.

The last stage of the upgrade is clean up so I am assuming that this will free up some space.

Another option is to buy a bigger hard drive :razz:

---

