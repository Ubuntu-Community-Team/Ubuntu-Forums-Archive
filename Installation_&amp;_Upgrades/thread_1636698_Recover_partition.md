---
title: "Recover partition"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by Hsiu on 2010-12-03
Okay, I f-ed myself.

While installing, I accidentally chose a data partition I had (NTFS, I believe) to be the swap partition after the installer complained that I hadn't picked a partition for the swap.

So, that fubared it.

I've read lots online about using parted or testdrive or various EASEUS products to recover 1) data from jacked partitions 2) deleted partitions.

BUT, will any of these, or another method, allow me to revert that partition back to the NTFS one it was, with the data hopefully still in tact?

Right now, if I try testdisk for instance, it sees it as a linux swap partition. and I assume simply changing the (T)ype back to NTFS will just produce a fresh MFT, leaving my old data there all mushed up together with nothing pointing to it.

I haven't run Ubuntu since doing this, I booted right back up into Vista, so very little should've been written there. Most of the data should be okay, but the metadata might be jacked beyond recovery. Still, it'd be nice to try and just put it back how it was - any chance of this? Can anyone suggest how I do that?

---

### Post by Quackers on 2010-12-03
There may be some info about that here

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

