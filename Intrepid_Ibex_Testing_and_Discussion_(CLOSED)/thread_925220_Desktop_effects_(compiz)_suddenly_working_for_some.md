---
title: "Desktop effects (compiz) suddenly working for some ATI users..."
date: 2008-09-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Mazza558 on 2008-09-20
I restarted after an Xorg update and got Desktop Effects straight away. They're quite slow (especially scrolling images), but I assume this is the work of the Radeon driver?

---

### Post by scradock on 2008-09-20
I noticed this too, a few days ago. Unfortunately, it has now decided NOT to work - screen freezes with jagged artefacts, and I cannot invoke any action except Power Off.

Intrepid alpha5 updated to current, ATI Radeon Xpress 200m (5955), with ati driver. Haven't been able to use compiz since early Hardy, so I was rather excited to begin with.

One strange thing - it now appears to be possible to have parts of the compiz effects working without others: I could have Animations working but not Desktop Cube and Cube Rotate, despite both being enabled in ccm. In the past it seemed to be more all-or-nothing, IIRC.

Ah well, try again later. For now I have apt-get removed compiz-core and its dependencies.

---

### Post by bpl07 on 2008-09-20
> **Mazza558 said:**
> I restarted after an Xorg update and got Desktop Effects straight away. They're quite slow (especially scrolling images), but I assume this is the work of the Radeon driver?

Compiz must have stopped blacklisting the opensource ati driver by default.  I've had desktop effects for a while now by disabling the blacklist check.  My system grinds to a halt after an hour of compiz though so I'm sticking with metacity until we get fglrx working again.

---

### Post by Sand &amp; Mercury on 2008-09-23
I'm using the Mesa driver for now and it defaulted to using Compiz at first, until I disabled it, then it said it couldn't be enabled again. I figure that since it's defaulting to Compiz, it's ignoring the driver blacklist at first till you try to enable it yourself.

---

