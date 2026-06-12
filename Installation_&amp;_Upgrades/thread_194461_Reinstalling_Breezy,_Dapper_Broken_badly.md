---
title: "Reinstalling Breezy, Dapper Broken badly"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by mlwmohawk on 2006-06-11
(1) Additional IDE/ATA or SATA interface cards confuse IDE scan order and
your previous /dev/hda becomes /dev/hde this causes "Waiting for root" message.

(2) Two display cards. I had an ATI Radeon AGP card as well as a PCI Rage
Pro PCI. In breezy badger these were configured and worked using Xinerama.
When I installed Dapper Drake, the computer hangs/crashes. Yes, I'm sure it
is a "new" radeon ATI driver issue, but come on, it used to work! The test:
I can run single screen with the AGP radeon card, it works fine. I set it
up to work with the RagePro PCI, it crashes. I remove the Radeon card, the
PCI card works. I put both back in and use the 2.6.12 kernel from Breezy,
it works. Use the 2.6.15 kernel, it crashes.



I think Linus was right, the 2.6 kernel needs some stabilization time.

---

