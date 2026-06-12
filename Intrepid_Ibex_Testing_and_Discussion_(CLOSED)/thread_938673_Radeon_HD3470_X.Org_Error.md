---
title: "Radeon HD3470 X.Org Error"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ukaratay on 2008-10-05
Hi all,

I have Asus M51Se240DV notebook with 3GB RAM and Radeon HD3470 graphic card. The kernel has a problem with 3GB RAM and I solved it with a line at booting "mem=2900M". However, I have another problem with my graphic card. When I tried to start x it gives errors:

(EE) RADEON(0): Not valid linear framebuffer address
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
giving up

P.S. It's live CD and I'm at the stage of installation.

---

### Post by forumache on 2008-10-05
radeon hd3470 is not yet supported (as many others).
the binary drivers do not yet support X.org 7.4
so yes, it might have worked with hardy, because hardy had an older X.org
let's hope that either ATI/AMD will release a new Catalyst this month with support for X.org 7.4, or that radeon/radeonhd will support this card.

2 days ago I bought an HD3450 (on AGP) and I'm still waiting to install it.

---

