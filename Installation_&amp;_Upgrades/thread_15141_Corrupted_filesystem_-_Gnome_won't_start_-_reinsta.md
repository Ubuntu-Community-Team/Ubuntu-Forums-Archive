---
title: "Corrupted filesystem - Gnome won't start - reinstall?"
date: 2005-02-12
forum: Installation &amp; Upgrades
---

### Post by adamvert on 2005-02-12
Hi

I have a laptop with XP, Ubuntu (all on one partition), and several data partitions.  Yesterday I was trying to move partitions in Windows with Partition Magic, and it threw out an error while moving the Ubuntu root partition.  I rebooted, and... got no further than GRUB, which gave me an "Error 17", presumably because it couldn't read the Ubuntu root partition.

Fortunately I had a Knoppix live CD kicking around, so I booted off that and used the fantastic testdisk utility to rescue the Ubuntu root partition.

Now I can read files, and I can boot off it, but when trying to start Gnome, I get this error:

```
error while loading shared libraries: /usr/lib/libz.so.1: invalid ELF header
```

I've run fsck, and gone through hundreds of errors, lost inodes, etc (just saying yes to everything), but I'm still getting this error.  I guess that there are probably plenty more where that came from too...

So the question is, do I just wipe the partition and reinstall, or is there a way of repairing all the broken files?  Or will I just keep on finding corrupted files in dark corners?

TIA for any and all advice,
Adam Butler

---

### Post by scoon on 2005-02-14
Hey there, 

If you don't have any kind of "commitment" to this current installation.... Unfortunately, I would suggest that you just re-install.  THat is a pretty crappy solution but it will be better than finding broken libs later on down the road when you really need to rely on this. 

scoon

---

### Post by Jad on 2005-09-23
I have same problem, formating disk is not a problem at all, but maybe telling us why this is happening to avoid it next time.
Thanks

---

### Post by mlomker on 2005-09-23
>  us why this is happening to avoid it next time.

In the original poster's case the problem was Partition Magic, not Ubuntu.

If you install the **apt-file** package it'll allow you to easily search for what package a particular file belongs to.  With that information you could then force a reinstall for that package to fix your problem.

I think in this case you'd be a lot better off reinstalling.  You will keep finding bad files in dark corners... ;-)

---

### Post by Jad on 2005-09-23
That was tricky! never heard of apt-file before
thank you, i'm apting now

---

