---
title: "ATI FireGL Mobility T2 in Ubuntu 9.10?"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by trailbound on 2010-01-30
So I've been reading forum post after forum post and seem to be seeing conflicting answers. Can anyone confirm for me... are there drivers available (open source or otherwise) in Ubuntu 9.10 that supports 3D for an ATI FireGL Mobility T2 card?  

I'm running on an old IBM T41p with that card and have held off upgrading since Ubuntu 8.10 because I understood that support was dropped for my video card from fglrx and that none of the open source drivers did 3D support. Has that changed?  Can I safely upgrade to 9.10 and get my 3D support back? or will I have to be content with 2D via open source drivers?

Thanks! :)

---

### Post by Mark Phelps on 2010-02-01
The open source drivers provide SOME 3D acceleration, but nowhere near the amount provided by the restricted drivers -- which, as you have already discovered, were discontinued by ATI.

If you have restricted drivers installed now, when you "upgrade" to 9.10, don't be surprised if you get a black screen and a flashing cursor -- and no desktop.

Your best bet would be to remove the restricted drivers and replace them with open source before you do the upgrade.

And, in case you're curious, the alternatives of downloading the source and/or using EnvyNG simply won't work.  It's a basic conflict between ATI restricted drivers and the newer Xorg versions.

Open source is your only option with Ubuntu's newer than 8.10.

---

