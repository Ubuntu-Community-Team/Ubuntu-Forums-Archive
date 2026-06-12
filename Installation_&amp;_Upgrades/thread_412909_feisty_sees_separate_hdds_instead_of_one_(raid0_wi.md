---
title: "feisty sees separate hdds instead of one (raid0 with nforce430)"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by super7 on 2007-04-18
hello,

I have an Asus M2NPV-VM board with nforce430 chipset onboard and 3 sata drives connected to a raid 0 stripeset via the nforce raid bios. the drives(!) are recognized ok when trying to install feisty but as separate drives (3 times 40gb and not one 120gb drive). it works on winxp (showing only 1 drive with 120gb). on the first drive linux shows me the "correct" partitioning of the whole raid set, the other twos don't have any partition information.

afaik feisty includes proper nforce430 drivers but do I have to set something special in the bios or when starting the installation? i wonder that nobody else has this problem ... searched google and this forum but didn't find anything related ... did I overlook something?

I had the same problem with a dawicontrol pc-133 4port ide controller (edgy) (with same motherboard, seeing 4 drives) but didn't experience this problem with ubuntu edgy 6.10 on a HP netraid-3si controller (raid 5 on a different motherboard, seing correctly 1 drive and not 6) ...

thank you,
claus

---

### Post by SodiumKPump on 2007-04-19
Hi, I have a similiar situation.  I have 3 idential western digical 120 gb SATA drives, two of which are RAID 0 striped.  I installed feisty to the third drive as I still have a windows installation on the stripe--I was wondering if there is a way I could access my stripe from Ubuntu.  My motherboard is DFI lanparty running nforce. Thanks!

---

