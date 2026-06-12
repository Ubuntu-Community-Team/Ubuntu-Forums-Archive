---
title: "Dual Boot, with installing Windows Second?"
date: 2007-03-09
forum: Installation &amp; Upgrades
---

### Post by asgardfleet on 2007-03-09
Hey

Just wondering if it is possible to have Ubuntu installed first and then to be able to dual boot by installing Xp or Vista.

I know that both of these seem to overwrite the MBR.  But is there a way to some how save it before hand, or edit it manually later to allow both OS's to boot.

Thanks

---

### Post by confused57 on 2007-03-09
> **asgardfleet said:**
> Hey

Just wondering if it is possible to have Ubuntu installed first and then to be able to dual boot by installing Xp or Vista.

I know that both of these seem to overwrite the MBR.  But is there a way to some how save it before hand, or edit it manually later to allow both OS's to boot.

Thanks
With 2 hard drives, it wouldn't be a problem...with one hard drive, it's better to have Windows on a partition preceding the Ubuntu partition.
I have seen other posters report they have installed Windows  on a partition located after the Ubuntu install partition, Windows would overwrite the mbr, but grub was reinstalled, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

You're taking a chance that your system won't work set up this way(Ubuntu/Windows)...most people would recommend Windows/Ubuntu, which "should" work with no problems.

---

### Post by asgardfleet on 2007-03-10
Thanks,

In the past that is all I have done, installing windows first, though I am sort of wanting to have Ubuntu now and then possibly installing Vista later on...

But thanks for that if I do decide to do it I know that I can install grub over the MBR again.

---

