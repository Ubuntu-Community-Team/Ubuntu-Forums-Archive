---
title: "Upgrade Dapper -&gt; Feisty but update-manager only offers Edgy"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by zoubidoo on 2007-05-06
I'm trying to do an upgrade from Dapper to Feisty on an i386 platform.  I have a Feisty cdrom (the non-bootable type).

I ran software-properties and did "add cdrom".  It was correctly recognised as Feisty:
cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)] / feisty (binary)
Then:
```
sudo gksu "update-manager -c"
```
It reports: "New distribution release '6.10' is available"  But I'd expect it to say 7.04

Does 6.10 need to be installed first or is it possible to go straight to 7.04?

Thanks for any suggestions.

---

### Post by Tux Aubrey on 2007-05-06
> Does 6.10 need to be installed first or is it possible to go straight to 7.04?

Yes - too big a jump from 6.06 to 7.04.  Its either a two step process or a clean install, I'm afraid.  I you do decide to do a clean install, I'd suggest ensuring your /home has its own partition.

---

### Post by zoubidoo on 2007-05-06
Many thanks!  And I definitely agree with the /home partition tip.

All the best,
Z.

---

