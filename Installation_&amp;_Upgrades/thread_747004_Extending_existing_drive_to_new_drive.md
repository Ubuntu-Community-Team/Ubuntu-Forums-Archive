---
title: "Extending existing drive to new drive"
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by Brigtitan on 2008-04-06
I have a drive 8gb, that I install ubuntu on, and have now added a 80gb drive to the ide chain..

how can I extend the existing drive to begin using the other drive's space?  I want it to appear there is just one drive.

Thanks in advance, 

Brig

---

### Post by .nedberg on 2008-04-06
You could look into LVM
[http://tldp.org/HOWTO/LVM-HOWTO/](http://tldp.org/HOWTO/LVM-HOWTO/)
and
[http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm)
helped me when I first sat it up. It is not easy though, and I don't see the need on a normal desktop.

I recommend you move your /home to the new drive instead. That would also make reinstalling easier.

---

