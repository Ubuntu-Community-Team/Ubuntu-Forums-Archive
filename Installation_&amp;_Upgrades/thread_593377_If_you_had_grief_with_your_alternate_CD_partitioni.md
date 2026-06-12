---
title: "If you had grief with your alternate CD partitioning"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by deusxechelon on 2007-10-27
I used the guided partitioning on my first attempt at Dual Booting XP and Ubuntu which ended up in a miserable and most unrecoverable failure (Boot Failure when I tried to boot both operating systems, windows recoveries and testdisk could not fix it) requiring me to wipe the drive and start over. Fortunately it was a fresh install so it was just a loss of time and not data.

If this happened to you and you still want to successfully dual boot heres what I did:

I used a liveCD that I had on hand which I use for recovery known as [Parted Magic]("http://partedmagic.com/") to delete the partitions left over from the disaster and installed Windows again. After that I loaded Parted Magic again and premade the linux partition and the extended swap partition.

So far so good? Good, put in the Ubuntu Alternate CD and when you make it to the partitioner, go with MANUAL. All you have to do here is input the same thing you did with GPARTED from Parted Magic (Irritating in text, I had no choice.. the ubuntu livecd wouldnt work for me) into this here gparted. Before you tell it to perform the actions, make sure Windows has the boot records ( B ) and the partition you want linux to go in is designated with Root ( / ).

After that sit back and enjoy ubuntu. I hope this helped somebody.

---

