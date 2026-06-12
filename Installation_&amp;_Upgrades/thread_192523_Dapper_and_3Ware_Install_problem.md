---
title: "Dapper and 3Ware Install problem"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by lborkey on 2006-06-08
Upgraded my nice and stable breezy to dapper.  Went ok but I subsequently made a mess of some other things.  So I figured I'd do a wipe and reload from scratch.

I have a 3Ware 4-port PATA card with 4 300GB drives.  RAID 5 was too slow for MythTV so I converted to RAID 0 for a single 1.2 TB drive.  Ran fine under breezy, no problems partitioning or installing.  When I upgraded breezy to dapper, dapper also ran pretty well.

Upon the fresh install, dapper's partitioner reports the drive as having negative space, that is, free space shows up as a large negative number.  It tries to partition but keeps failing with a **No root file system** message and won't continue.

If I reconfigure the array to be two 600GB drives, seems to work fine as does a 900GB array with a hot spare left over.  Seems that dapper ain't hip to the terabyte scene.  Anybody else see this problem or better yet, my obvious stupidity in missing something trivial.  Please heap your n00b derision upon me if you have an answer, I'm not proud.

---

### Post by lborkey on 2006-06-08
Another note, I was running ext3 if that makes a diff.  Doesn't seem to have even gotten to that point however.

---

