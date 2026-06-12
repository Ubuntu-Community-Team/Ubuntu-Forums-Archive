---
title: "[SOLVED] 6200 - 6800EX question"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by Merovius on 2008-01-05
I have replaced my nvidia 6200 256mb video card with a 6800EX 256mb video card. Ubuntu (Gutsy) still shows it as a 6200 under Hardware Information. If I  do a lspci (sp?) it shows as NV44A 6200.

How to get it to show the right card? I tried the sudo dpkg-reconfigure thing and spent a half hour getting my system bootable again.  Would reinstalling the restricted driver correct it?

How will it affect the performance if it's seen as a 6200?

I ran glxgears and at full screen I'm getting 47 fps!  I think I'm taking a hit from this incorrect recognition of the card.

TIA
Steve

Boy do I feel stupid... While switching out video cards yesterday, wife required attention, came back to finish what I was doing and apparently put the 6200 I had just removed, BACK IN! No wonder Ubuntu says it's a 6200. It IS.

Today (with dear wife at work) 6800EX is in now and of course recognized as a 6800EX.

glxgears at full screen is now getting 147 fps.

Go ahead laugh...
Steve
:lolflag:

---

