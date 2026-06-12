---
title: "Ubuntu Restricted Drivers Manager Bug?"
date: 2007-08-20
forum: Installation &amp; Upgrades
---

### Post by watermark on 2007-08-20
I was installing feisty for a friend, so he hooked the computer up.  It installed fine, then I noticed that the Restricted Drivers Manager said he had an nvidia card.  So I chose to install the restricted nvidia drivers.  Then X wouldn't come up.

Turns out that he had an nvidia card, but had the computer plugged up to the on-board Intel video, but the nvidia drivers still installed and replaced the Intel driver in xorg.conf to the nvidia module.  I understand that it's hard to run an intel card with nvidia drivers ;), but should they have even installed in the first place?

I know enough to do the whole lspci, edit xorg.conf dance, but the common user probably wouldn't.

Just my thoughts.

---

### Post by wolfen69 on 2007-08-20
the onboard video should have been disabled by going into the BIOS first, before installing. try that. personally, i would just re-install. it only takes 15-20min.
make sure that onboard video card is disabled.

---

### Post by watermark on 2007-08-20
I was able to fix the problem by disabling the on-board video and changing the PCI number.

What I was saying is that the Restricted Drivers Manager probably shouldn't have overwritten an Intel driver, but produced an error.  It should probably only overwrite an entry that has the Driver listed as "nv".  I'm not familiar with the other restricted video drivers, but there should probably be similar checks for other drivers.

---

