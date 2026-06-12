---
title: "Removal of Ubuntu from USB drive"
date: 2012-02-07
forum: Installation &amp; Upgrades
---

### Post by WariusBirde on 2012-02-07
Hello,

I received a USB drive with a custom build of Ubuntu a few years ago for a programming class I was taken. Since then, the kernel or something else became corrupted due to the drive being bumped out of place during use. Since I have a partition set up on my computer now I've decided to revert the USB to its original nature.

However, the USB drive does not appear when I go into my other OS (Win 7) and I can't figure out how to get it to appear so I can format the thing; however I can locate it in the device manager as a flash drive and in the drive manager. Google doesn't produce any results that corresponds to my situation, so I'm at a loss. Please forgive my ignorance, but I don't know what to do and I'm concerned that I'll end up bricking the drive.

Any help on how to go about removing the Ubuntu partition and restore the drive to a conventional USB drive would be greatly appreciated.

---

### Post by ottosykora on 2012-02-08
my guess:

it is formated as ext3 or similar, so windows will not know about it really.

You will probably need some linux formating tool. Try some live CD , can be ubuntu itself or something slim like partedmagic and there you run gparted and delete the existing partition and create a fat32 partition then.

You could also try in windows to look in device manager /drives and you may see it there with 'unknown' partition. You could delete it or change it to fat32.

If all this fails, then the device might be defective as well and you can trash it.

---

