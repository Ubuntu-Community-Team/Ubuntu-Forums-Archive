---
title: "Upgrading to karmic when it's out..."
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Hagar55 on 2009-10-17
Right now I'm running Jaunty in dual boot with windows Vista on my Dell studio 17.
Now Jaunty isn't running perfectly, compiz has to stay switched off because the Radeon HD mobility 3650 doesn't support it.

I have been thinking to upgrade to Karmic when it comes out, however...
Right now I'm runnning on ext3 I would like to try ext4, do I best change the filesystem before or after upgrading to Karmic ?
I read that only new files benefit from the speed increase, does upgrading the distro files (and rewriting them) count as newly written files ?

---

### Post by slakkie on 2009-10-17
> **Hagar55 said:**
> Right now I'm running Jaunty in dual boot with windows Vista on my Dell studio 17.
Now Jaunty isn't running perfectly, compiz has to stay switched off because the Radeon HD mobility 3650 doesn't support it.

I have been thinking to upgrade to Karmic when it comes out, however...
Right now I'm runnning on ext3 I would like to try ext4, do I best change the filesystem before or after upgrading to Karmic ?
I read that only new files benefit from the speed increase, does upgrading the distro files (and rewriting them) count as newly written files ?

I don't think an upgrade will rewrite the files like you think. It will make a copy, but the inode information will stay the same, an example:

```

$ stat -c "%i %n" x
1508883 x
$ cp x x.x
$ stat -c "%i %n" x x.x
1508883 x
1509001 x.x
$ cp x.x x
$ stat -c "%i %n" x x.x
1508883 x
1509001 x.x

```

As you can see the inode hasn't changed at all. I assume the new file needs to have a different inode before it can be used with all the new ext4 extra's. Unless x gets removed first and then copied, but I don't think that is something the installer does..

---

### Post by Hagar55 on 2009-10-17
So I have to wipe everything and start anew ?

---

### Post by Hagar55 on 2009-10-18
If I do only upgrade, does it make sense to change to ext4 ?

---

### Post by mick222 on 2009-10-18
Better to do a new install backup all you files and then reinstall them.Maybe when you install karmicv you could set up a seperate home partition saves wiping it when you upgrade next time.

---

### Post by slakkie on 2009-10-19
> **Hagar55 said:**
> If I do only upgrade, does it make sense to change to ext4 ?

Depends, if you want to make use of all the new ext4 features then it makes no sense to me. Plenty of files will still be ext3 and you will not benefit from all ext4-features. I would, if you want to convert to ext4 install Karmic, rather then upgrade from Jaunty.

---

### Post by Hagar55 on 2009-10-19
I have a seperate home partition, but if I want to upgrade to ext4 I have to wipe that *** well so I would really be starting from scratch again...

---

### Post by NCLI on 2009-10-19
> **Hagar55 said:**
> I have a seperate home partition, but if I want to upgrade to ext4 I have to wipe that *** well so I would really be starting from scratch again...
No, you can just backup all of your files before you format it ;)

---

### Post by philinux on 2009-10-19
> **Hagar55 said:**
> I have a seperate home partition, but if I want to upgrade to ext4 I have to wipe that *** well so I would really be starting from scratch again...

I've been deliberating this for months. I've got 2 HD's. Jaunty on one and karmic on two. I always have the development version on 2. I copied my home on to the karmic disk and I have to say accessing files and things like creating thumbnails is very snappy.

I've decided this. Karmic to me is unlike any before, as I've usually just upgraded. But with Ext4 and grub2 to name just two major changes, to me my choice is clear. For me I've decided to wipe my number 1 hard drive and start from scratch then copy back my home from disk 2. Anyone else with one hard drive could use another backup facility. 

I'll sort out dual booting with grub2 later. Legacy grub is gone as far as I'm concerned.

---

