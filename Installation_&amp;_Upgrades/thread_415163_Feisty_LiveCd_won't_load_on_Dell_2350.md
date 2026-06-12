---
title: "Feisty LiveCd won't load on Dell 2350"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by RickThorpe2006 on 2007-04-20
This is a Dell Dimension 2350 with the Intel Integrated Extreme 3D Graphics on the motherboard.  The 6.10 LiveCD loads fine so long as you (a) use F4 to select 640 x 480 and (b) use the safe graphics mode to load.  Neither of these options nor the usual suspects in additional command line options through F6 will get Feisty to load.  Has anyone had any success loading the Feisty LiveCD on this or a comparable machine?

---

### Post by rich.bradshaw on 2007-04-20
I have a Dell inspiron 8100 - it takes ages to boot, but it does eventually.

Try pressing ctrl-alt-f1 whilst it is booting - I think this only works if you can get into a graphical part, but ti will show a different tty that on mine had some error messages.

Mine takes around 10 mins to boot from CD as it has an error with fd0 apparently. Once installed it's fine and quick again.

---

### Post by RickThorpe2006 on 2007-04-21
Solution was to F6 into additional command line options, delete "xforcevesa" and replace it with "lowres"

---

