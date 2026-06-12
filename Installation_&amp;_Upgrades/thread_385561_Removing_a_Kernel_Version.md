---
title: "Removing a Kernel Version"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by webworldx on 2007-03-15
Hi there,

I've been playing about with Ubuntu over the past few days, but the laptop crashed half way through rebuilding linux-source (among doing other things that day).  The result on next boot was Ubuntu loading fine, but now device manager only recognises a single CPU instead of my two, and the graphics card being incredibly slow.

It's been all fine as i've just selected the second kernel version down on the GRUB list and loaded that, then deleted the two top options from the GRUB list - my two CPU's are back and BilliardGL loads perfectly fine - but I am wondering how to delete the "faulty" kernel version 2.6.18-4-486 (i'm back on 2.6.17-11-generic now) completely, and/or reinstall the later one for use.

Also just wondering, if I leave it there untouched, when the next kernel version upgrade happens and i'm running on 2.6.17-11, will it take the faulty 2.6.18-4 settings or the one i'm currently using to upgrade to?

Thanks a lot guys!

---

### Post by Kateikyoushi on 2007-03-15
You can remove the old kernels with synaptic. System > administration > synaptic.
Then check the packages with Installed local or obsolate status in the laft frame.

---

### Post by webworldx on 2007-03-15
Of course! Should have looked there first. Thanks a lot.

---

