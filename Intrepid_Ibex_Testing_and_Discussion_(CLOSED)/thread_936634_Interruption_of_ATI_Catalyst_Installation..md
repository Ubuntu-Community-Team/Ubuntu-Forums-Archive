---
title: "Interruption of ATI Catalyst Installation."
date: 2008-10-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Grimhound on 2008-10-03
I'm trying to set up my gaming box with Intrepid to give it a stress test, yet I've run into a snag. When I try to install ATI Catalyst from the Add/Remove Programs, I get the following:
> Cannot install 'fglrx-amdcccle'

This application conflicts with other installed software. To install 'fglrx-amdcccle' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

Any idea what I need to take out to make it so Catalyst can be installed?

---

### Post by wgrant on 2008-10-03
ATI have failed to update fglrx (their proprietary X video driver) to work with Intrepid's version of Xorg. You will have to use the open source ati driver for now.

---

### Post by Grimhound on 2008-10-03
> **wgrant said:**
> ATI have failed to update fglrx (their proprietary X video driver) to work with Intrepid's version of Xorg. You will have to use the open source ati driver for now.

What open source ATI driver, if I may so inquire?

Currently wrestling with the issue of my audio not working and the potential that the 4850 isn't even being recognized by the system. Almost curious if it's a conflict with the motherboard.

---

### Post by RAOF on 2008-10-03
The open-source driver is the driver you're (probably) using now; it should handle 2d and possibly dual-head, but won't support 3d or 2d acceleration.

Given that you've got a GUI, I think it's a fair bet that your 4850 *is* being recognised by the system :).

---

### Post by Grimhound on 2008-10-03
> **RAOF said:**
> The open-source driver is the driver you're (probably) using now; it should handle 2d and possibly dual-head, but won't support 3d or 2d acceleration.

Given that you've got a GUI, I think it's a fair bet that your 4850 *is* being recognised by the system :).

Oi. Guess I'll just have to wait until the issue is resolved or forestall my plans until things are fixed. Wish something would just work for once. Well, now I just need to figure out how to get the audio working on the desktop. Funny that the laptop needs so little coaxing and it's the desktop that gets fussy with these things.

---

### Post by Bal_Zac on 2008-10-03
I am not sure if it is possible, but you could try to downgrade to Xorg 7.3 (Intrepid uses the *just* released 7.4 ).
Just released on September 23:  [http://www.phoronix.com/scan.php?page=article&item=xorg_74_final&num=1](http://www.phoronix.com/scan.php?page=article&item=xorg_74_final&num=1)
With AMD's latest track record I would expect to wait a few weeks until their next driver update for 7.4 support, but then again ya never know.

---

