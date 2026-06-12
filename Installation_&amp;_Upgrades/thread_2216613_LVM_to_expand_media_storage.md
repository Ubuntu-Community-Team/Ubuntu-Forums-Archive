---
title: "LVM to expand media storage"
date: 2014-04-12
forum: Installation &amp; Upgrades
---

### Post by lewisbraid on 2014-04-12
I have a media PC running Ubuntu, and would like to merge a new HDD with an full HDD. My hard drive setup is as follows;

1 - OS
2- Media Storage (full)
3 - Media Storage (empty)

I would like to merge drives 2 and 3, so all my media is on one larger drive, taking on the media (from drive 2) and folder structure - Am I right in thinking LVM is the way forward? If so, how do I do this? 

Hopefully someone can either walk me through, or point me in the direction of a tutorial.

Thanks!

---

### Post by TheFu on 2014-04-13
There are many opinions on this. If you have great backups, then using LVM in this way can work, however, know that if either of the HDDs fail, data on the other will be difficult to access.

Other options exist using file-system-merging tools that leave the files on separate partitions, but make a "view" that merges those together.  auFS is one of those tools. UnionFS is another and mhddfs yet another.  These do not relieve the admin from having backups, but often having smaller file systems to backup makes using older, smaller HDDs for that purpose easier.

Oh - and there are probably 20 other ways to achieve the end-goal you seek.  [SnapRAID]("http://snapraid.sourceforge.net/") might be useful too.

I wouldn't use LVM for this, unless I had great backups that could be restored. About 10 yrs ago, I lost 80% of my media using LVM in this way.  I still use LVM, just not spanning HDDs unless my backups are grade-A, perfect.  The normal situation with large-ish media collections is that backups don't happen, right?

I must point out that I do not use any of those tools in my media collection. Symlinks work well for me, plus adding a 4TB HDD as needed isn't a big deal (always buy 2; backups, right?).

---

### Post by frostschutz on 2014-04-13
I use LVM everywhere and am very happy with it. It's a great tool, provided you're willing to learn how to use it. As for backups, you need them in any case. What do you do when your disk dies or you delete/damage some files by accident?

Adding LVM to a disk that is already full might be complicated, depends on the exact partitioning (show your parted -l or similar?); traditionally you'd put LVM on a new disk, copy data over, and once everything is copied and verified, format the old disk and make it a member of your LVM. Then grow the LV and the filesystem if you like.

Depending on how you want your media organized you can also work with multiple volumes, like one each for photos, movies, music, ...

> I lost 80% of my media using LVM

Without LVM, many people end up resizing and moving partitions at some point, using gparted... then the system crashes and whoops, data gone.

Hence, regardless what you decide on: backups, backups, backups.

---

