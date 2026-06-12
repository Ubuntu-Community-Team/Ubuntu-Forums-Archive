---
title: "Dual Boot mount partitions"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by Curio21 on 2007-09-13
I am trying to create a dual boot xbuntu 7.04 / Windows 98 system.  I used Paragon partition manager to create a separate primary partition. When I began installing Xbuntu all was well until near the end when I received the message:

"installer nees to commit changes to partition tables, but cannot b/c partitions on the following mountpoints could not be unmounted

/media/LIN/040sys"


"Lin" is what I named the volume that I created with Paragon to install xbuntu.  LIN sits next to my other primary partition upon which win 98 is installed. The program offers to attempt an unmount, but fails and throws me back to the beginning install screen.  Any idea's?  I am not a newbie, but also am not that experienced either.  I am coming close to just installing a second HD,but would like to try and give dual boot one more shot.  How would I unmount a mountpoint?  and if I did, would'n't I lose the ability to continue installing xbuntu?

Thanks,
Curio21

---

### Post by unperson on 2007-09-13
Hi Curio,

I don't actually have a lot of relevant experience, but it seems to me if you're going to write changes to the partition table I'd think that those partitions would need to be unmounted.  That doesn't mean you can't write to them, you can still write to the block device (/dev/hda or whatever).  It's just that they won't be an active part of the filesystem, which makes sense if you're going to make structural changes to them.

How are you making the changes?  With a live CD?

Anyway, that's just my 2 cents so please take it with a grain of salt.

---

