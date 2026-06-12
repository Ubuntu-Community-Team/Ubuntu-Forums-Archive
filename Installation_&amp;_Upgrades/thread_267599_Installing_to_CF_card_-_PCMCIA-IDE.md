---
title: "Installing to CF card - PCMCIA-IDE"
date: 2006-09-28
forum: Installation &amp; Upgrades
---

### Post by mafu on 2006-09-28
I've just done an install from live cd to the CF card in my Vaio UX17 and can't get it to boot properly. /boot is second partition on the hard drive (hda2) with the rest left to winXP which still works fine, and hdc1 is the / partition on the CF card. Grub comes up fine but when I try to boot (other that for xp which is ok) it starts to boot then sits waiting for root partition and eventually fails.
I've done some digging and it looks like the CF card is accessed as a PCMCIA - IDE drive, so it looks like I need to get the correct drivers loaded before booting - I've tried following some pcinitrd instructions I found 'lying around' but no joy so far. 
Anyone done this/got any ideas? I've been banging my head against it for a while. I really want to get it up and running - it looks pretty damn good from the live-cd so I'm keen to get into it.


TIA
Mafu.

---

