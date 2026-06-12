---
title: "Fat32 partition not working properly"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by peap on 2006-06-01
I made a clean install of 6.06 today on my new hard drive. During the install I also had my old "second" drive connected as usual (I use this one for storing movies etc.) My old "first" drive is out of the picture.

The second drive worked just fine before when used breezy badger. Now Gparted recognize it as a fat32 partition it cannot reach of some reason. It's not beeing mounted properly. The dapper installation seems to have done something wierd here.

I also have a third disk very similar to the second one and that one still works like a charm, that's what's getting me kind of worried.

Any other approaches except for sadly looking at the gparted screen? There's som really important stuff on that disc...

---

### Post by aysiu on 2006-06-01
Maybe this will help?
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by peap on 2006-06-02
I booted with my old harddrive (breezy) and still the same problem. I then dualbooted into winxp, installed partition magic and the problem was there. I did no changes (as I couldn't, the partition was damaged), saved and booted into breezy. 

This time both fat32 partitions worked! Don't ask me why but it seems like partition magic. winxp shutdown or the breezy bootup fixed the problem. Quick as lightning I backed up all the important data. Thank god! I was really worried there for a moment.

Back into dapper (my new hard drive) and both disks was successfully mounted. Has anybody the slightest idéa of what could have happened here?

---

