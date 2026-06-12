---
title: "KK: Can install but cannot boot"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by XEyedBear on 2010-02-16
I need some advice on problem source identification please:    I have installed Ubuntu 9.10 on old hardware: Abit KT7A, 768 Mb, Athlon processor (1.4Ghz), Maxtor 40 Gb drive, Nvidia Riva TNT2 M64 graphics card, Sound Blaster PCI 128 sound card.    The standard graphics based Ubuntu 9.10 will not install ('decompressione error; system halted'). the text-based install works fine and goes to completion.    Boot shows a white Ubuntu logo for a minute or so, then a blinking cursor in the top left of the screen and then nothing more.  This behaviour is reproducible: I have performed the install twice.    The crazy thing is that previously the hard disk was a much older  4GB Maxtor, together with an ancient 4 GB Quantum Bigfoot drive. Text based install worked fine on this config.  booted and ran well (but was obviosuly seriously limited on disk space).  The old hardware also accepted Win 2000 without any problem.    Where do I start looking for the cause of the problem?

---

### Post by darkod on 2010-02-16
Graphics? Anything on google about support for this card? I personally have no experience at all with older hardware since I'm using ubuntu only recently.

PS. I haven't paid much attention to the bottom of the grub boot menu. Can you boot safe graphics mode or similar from there?

---

### Post by XEyedBear on 2010-02-16
Irrespective of what Google says about my graphics card, the system worked just fine with this card prior to changing the disks - suggesting that there is not a lot wrong with the Nvidia drivers in Ubuntu, or with the card itself (and I run it at 1600 x 1200 on a 19&quot; monitor).  As I said, nothing shows on the screen when I try to boot - so there is no GRUB boot option to choose from.

---

