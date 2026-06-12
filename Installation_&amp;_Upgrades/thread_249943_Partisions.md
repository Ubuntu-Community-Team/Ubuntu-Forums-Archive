---
title: "Partisions?"
date: 2006-09-03
forum: Installation &amp; Upgrades
---

### Post by Starcraftmazter on 2006-09-03
Hello.

I have a 60gb HD, and another 20gb one, which we will not consider for the purposes of this exercise.

Now, say 30gb of this hd are used by windows and related things.

1. Can Ubuntu partition the remaining say 25gb (leaving 5gb spare), and install itself there?

2. Will it then be possible to allocate from space from the windows partition to the Ubuntu partition?

3. Can Ubuntu view NTFS?

Thanks.

---

### Post by pyros on 2006-09-03
> **Starcraftmazter said:**
> 
1. Can Ubuntu partition the remaining say 25gb (leaving 5gb spare), and install itself there?

Yes. You can do it when running the installer.
> **Starcraftmazter said:**
> 
2. Will it then be possible to allocate from space from the windows partition to the Ubuntu partition?

My understanding is that gparted (which should be on the livecd) uses ntfsresize, and can be used to do what you want. But, I have not done this.
> **Starcraftmazter said:**
> 
3. Can Ubuntu view NTFS?

Yes.

**However**, when dealing with modifying partitions, *especially* with a proprietary file system, you should always backup anything you can't easily replace.

---

### Post by Starcraftmazter on 2006-09-03
Alright thanks.

---

