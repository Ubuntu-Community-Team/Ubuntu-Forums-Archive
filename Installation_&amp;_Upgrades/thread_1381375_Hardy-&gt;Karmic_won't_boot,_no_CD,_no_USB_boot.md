---
title: "Hardy-&gt;Karmic: won't boot, no CD, no USB boot"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by David Gerard on 2010-01-14
Here's a locked-room mystery for you.

Dell Latitude C610 laptop. Has no CD drive and doesn't boot from USB. Windows on the first partition, I put Debian Etch on from floppies for the second partition.

I upgraded Etch to Hardy. This worked fine, the system still booted fine.

I upgraded Hardy to Karmic. Whoops ... it won't boot now!

GRUB doesn't appear to recognise the UUID of the Ubuntu partition.

I managed to boot the laptop into Windows by telling GRUB by hand "chainloader (hd0,0)+1" - though of course I'll need to do that every time I boot it.

So. How do I tell GRUB to boot into Ubuntu? Remember: there's no CD drive, and it doesn't boot from USB. I could make up Debian Etch floppies again, if I thought they'd work ...

(I am told the problem is that Hardy uses GRUB 1 and Karmic uses GRUB 2. I shoulda known better than to assume an Ubuntu upgrade would actually be straightforward ...)

---

### Post by PRC09 on 2010-01-14
I dont know if you can actually upgrade from 8.04 to 9.10 directly.See upgrade notes at this link.....


[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by David Gerard on 2010-01-14
It wouldn't surprise me if you can't.

On the other hand, Ubuntu's dist-upgrade quality control is deeply, deeply incompetent. Even "supported" upgrades don't work half the time.

Debian does a *great* job of dist-upgrades, even quite whacky ones, so the blithering incompetence that Ubuntu has demonstrated over many years is odd, but will evidently never be addressed. I'm used to Ubuntu upgrades going badly wrong and requiring a wipe and reinstall.

Someone has suggested it's a problem with Karmic calculating UUIDs differently (no doubt for my comfort and convenience). Is this documented anywhere.

---

