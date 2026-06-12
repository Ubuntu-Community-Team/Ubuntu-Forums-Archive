---
title: "w7, xp , linux breaks w7 functions"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by ottosykora on 2010-06-06
I would like to inform about some strange experience:

Having multiboot with special grub partition to make things simple (using legacy grub in it)

primary w7
primary xp
primary w98se
logical ubuntu 10.04
logical debian 5
logical fedora12
logical grub
logical ... few data partitions

Grub legacy does the job correctly, when booting to w7, it will hide the other prim partitions (hide xp and w98, unhide w7) and so all works fine.

However w7 lost some of its nice functions.
System backup, the w7 own imaging function does not work, it will not create any image of the system partition any more and it will also not restore anything from earlier backups (!!) since it does scan the whole drive and when it finds hidden system partition on that machine somewhere, it will abort any operations.

Searched the error logs of w7, passed them to some MS advise forums and was clearly instructed that this is correct and the presence of any other bootmanager then the w7 one will disable those functions and there is no way to enable them again.

Hmm, will have to go back to some acronis for that, but did someone here stepped over this?

---

