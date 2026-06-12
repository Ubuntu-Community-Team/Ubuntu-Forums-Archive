---
title: "Newb question: why do some add-ons require image disc"
date: 2010-10-07
forum: Installation &amp; Upgrades
---

### Post by waldzinator on 2010-10-07
Hello,

Be gentle, as I'm relatively new to Ubuntu.  I've been using it for a few months now, with great results.  I usually use Synaptic for add-on installation, but due to some customization issues with installing VirtualBox, I wanted to install via the terminal.  I followed the directions on VB's site, and while it was installing the files, the terminal kept prompting me to insert my image disc.  I quit and went to install from Synaptic, which also prompted me to insert the disc (the dkms add-on seems to be the culprit).  I finally submitted, inserted the disc, and all was well.

I've noticed that I've had to do this once or twice before.  I'm assuming this is only necessary when add-on's affect crucial system files/settings (for lack of a better term).  Is this correct?

Thanks!

---

### Post by dabl on 2010-10-07
The default installation sets up the CD as a "software source" or repository.  You need to disable that particular repository, in synaptic.

---

### Post by waldzinator on 2010-10-07
Dabl, it is indeed checked under Synaptic.  Thanks a lot.  I'm good at losing installation discs, so this was a headache waiting to happen.

---

