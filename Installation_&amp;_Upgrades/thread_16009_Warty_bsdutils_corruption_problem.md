---
title: "Warty bsdutils corruption problem"
date: 2005-02-18
forum: Installation &amp; Upgrades
---

### Post by zak on 2005-02-18
Hi. I'm having trouble installing Warty on an IBM Thinkpad 600X. Both the installer and the CD verification function complain that bsdutils is corrupt. The ISO I have checks out:

[zak@600x zak]$ md5sum warty-release-install-i386.iso 
a491903a2d2197651864dec3836d85e0  warty-release-install-i386.iso

I've burned it three times, on two different computers at speeds down to 12x and get exactly the same error each time I try to install. I don't see an obvious way to get the packages from a mirror instead of the CD. Is there one?

---

### Post by Felipejane on 2005-02-18
You might take a look at this thread, way down in the Installation forum: Problem At Install;debootstrap Error. Several people had trouble at different places, but mine was in the same place as yours: BSDUTILS. One of the people in that thread concluded that the problem lay not in the CD image but in the partitioning of the hard drive (I think that was his conclusion). Check it out.

---

### Post by zak on 2005-02-18
Thanks for the tip. I changed the partitioning scheme to not have a seperate /boot partition and it worked fine. I'm not sure if the error message was totally spurious, or just not informative. I would like to report a bug, but I would prefer to know exactly what went wrong before I do that. This probably requires a little more investigation, which means I need to install again with exactly the same partitions as I had the first time.

---

