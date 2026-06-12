---
title: "Repartitioning issue on first install"
date: 2004-12-28
forum: Installation &amp; Upgrades
---

### Post by DeathX on 2004-12-28
Had this issue coem up on trying to repartition both a win2000 and a win98se system (ntfs and fat32 setups of course.)  Well I get most of the stuff configured than I get to the partitioning setup. On both systems i don't want to wipe the drives but repartition them, btu on both cases when i insert a number that the hardrive should use instead of the current, e.g. 6.2 gb instead of 7.4 the program goes into the background, and then it pops back to the main page of the manual partition setup.  Should this be happening? Using an Ubuntu install disk 4.10 I have a bunch of them should I possibly try a different disk? Any and all help is appreciated, thanks in advance.

---

### Post by jobezone on 2004-12-28
Hi,

the install CD partitioner doesn't have the feature to resize ntfs,vfat (or any partition format at all, i think), so you must first use an app to resize your partitions, and create a new one with the space left.

There is Partition Magic for windows, at a cost.
Myself, I used kurumin
 [http://www.guiadohardware.net/kurumin/](http://www.guiadohardware.net/kurumin/)
which is a liveCD of linux and kde, and has got qtparted in it, which is good for doing this.

This is a feature I would very much want to exist in the next version of ubuntu in a few months.

---

### Post by DeathX on 2004-12-30
I repartitioned with Partition Magic, my friend lent me an old demo copy.
Now onto new problems with hardware, oh goody.

---

