---
title: "Installing to HD"
date: 2014-08-04
forum: Installation &amp; Upgrades
---

### Post by anon_private on 2014-08-04
If I decide to install to the HD, and my disk has a few bad sectors, but they are not increasing, will the UBUNTU/KUBUNTU OS avoid these sectors?

Or is it best to reformat the disk prior to installation? - full format?

Or wiill UBUNTU/KUBUNTU effectively reformat the disk as part of the installation?

One other point:

Would I need to create a swap partition at install, or should I do this after installation?

I have 1 GB of RAM, what size should the swap file be?

Thanks

---

### Post by Rob Sayer on 2014-08-04
The ubuntu install will handle the swap and formatting itself.  It'll set the swap partition size to the same size as your RAM.

However I would not recommend unity or KDE in 1Gb.  My 1Gb netbook runs xubuntu 14.04.  At home I use kubuntu 12.04 but that's on a 4Gb laptop.  KDE is highly configurable ... for some users to a fault but I don't mind that ... and you can tweak it to make it run a lot faster.  But personally I wouldn't use it with less than 2Gb.  The only exception I know of to this would be if you have 1Gb RAM and also a 1Gb video card, but this isn't going to be the case very often.

It's not really possible to make too many recommendations beyond that without knowing the hardware details and whether you want to use the whole HD  or dual boot with WIndows.  But I don't see much point in using 12.04 now that the 14.04 LTS is available.

If it's going to be an all ubuntu install I'd highly recommend installing with a separate / (root) and /home partitions.  Then you can update or reinstall while keeping your program settings and data intact, though you should still have data backed up anyway.

This is probably not possible with dual boot because there's a limit to how many disc partitions you can have but otherwise just search something like "ubuntu install separate home partition".  It may sound daunting but it isn't that hard, and there are good guides.

Stick to the actual ubuntu sites for info/support whenever possible, and it almost always is.   There's a lot of stuff on blogs but a lot of it is out of date.

And actually one of the first things I'd tell a new linux user is that just because someone writes a blog with ubuntu advice does NOT mean they know what they're talking about.  Some are very good but some are really bad, and if you're a novice it's hard to tell the difference.

---

### Post by anon_private on 2014-08-04
> **Rob Sayer said:**
> The ubuntu install will handle the swap and formatting itself.  It'll set the swap partition size to the same size as your RAM.

However I would not recommend unity or KDE in 1Gb.  My 1Gb netbook runs xubuntu 14.04.  At home I use kubuntu 12.04 but that's on a 4Gb laptop.  KDE is highly configurable ... for some users to a fault but I don't mind that ... and you can tweak it to make it run a lot faster.  But personally I wouldn't use it with less than 2Gb.  The only exception I know of to this would be if you have 1Gb RAM and also a 1Gb video card, but this isn't going to be the case very often.

It's not really possible to make too many recommendations beyond that without knowing the hardware details and whether you want to use the whole HD  or dual boot with WIndows.  But I don't see much point in using 12.04 now that the 14.04 LTS is available.

If it's going to be an all ubuntu install I'd highly recommend installing with a separate / (root) and /home partitions.  Then you can update or reinstall while keeping your program settings and data intact, though you should still have data backed up anyway.

This is probably not possible with dual boot because there's a limit to how many disc partitions you can have but otherwise just search something like "ubuntu install separate home partition".  It may sound daunting but it isn't that hard, and there are good guides.

Stick to the actual ubuntu sites for info/support whenever possible, and it almost always is.   There's a lot of stuff on blogs but a lot of it is out of date.

And actually one of the first things I'd tell a new linux user is that just because someone writes a blog with ubuntu advice does NOT mean they know what they're talking about.  Some are very good but some are really bad, and if you're a novice it's hard to tell the difference.


Thank you for responding.

I have been using Ubuntu 12.04.2 LTS for ages as a live pendrive with very few problems. On the whole (few exceptions that I could not explain), I have had no RAM problems.

I am not trying version 14 because I know that it needs more RAM than ver 12, and ver 12 is still supported (LTS).

Best wishes

Ps. I am influenced by appearance, and the quality (sophistication) of the applications.

---

