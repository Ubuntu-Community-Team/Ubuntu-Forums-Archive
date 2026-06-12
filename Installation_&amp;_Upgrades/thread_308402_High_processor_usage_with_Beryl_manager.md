---
title: "High processor usage with Beryl manager"
date: 2006-11-28
forum: Installation &amp; Upgrades
---

### Post by Duwi on 2006-11-28
Hi,

I managed the transformation from Suse 10.1 to Edgy and I am pretty happy since everything seems to work on my T60.

While searching around, I noticed this webpage

[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

Here, a installation of Beryl is described on a T60. And it looked all pretty cool, so I installed
Again, everything seems to work just fine.

BUT when I actually log into my computer using a XGL session, one of my processors is constantly running at 50 or 100%, causing the frequency scaling to jump up and down.

This happens in "battery" and also "ac-power" mode.

SInce it considerably shortens my battery life, I decided to deactivate the  beryl-manager at start up. The issues where resolved.

My question, is the high processor load normal when using the Beryl-manager?
Is there an additional setting that I have forgotten to change/modify.

Any help would be really appreciated.

thanks in advance

---

### Post by catanzag on 2006-11-28
If processor load is different from 0 even if you don't do anything (move windows, cube, ...) it's no normal;

however, I had the same problem at my first beryl install, but it was due to multiple beryl session erroneously started and the presence of previous installed compiz; then I remove compiz, I restart X (ctrl-alt-bksp) and everything now work fine.

if you search **howto beryl** on ubuntuforums you can find lots of guides with all distros, graphic cards and Xgl or AIGLX; you could check if something is slightly different from the guide you used

hope this can help

regards

catanzag

---

