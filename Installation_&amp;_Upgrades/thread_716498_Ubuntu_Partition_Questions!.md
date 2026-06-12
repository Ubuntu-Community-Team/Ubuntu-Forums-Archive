---
title: "Ubuntu Partition Questions!"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by AvengingKnight on 2008-03-06
what are the different Partitions in linux used for? and how does one take advantage of them? I have erased XP and installed Ubuntu 7.10 using /ext3. a separate drive using /USR and another as /swap. I'm a noob in Ubuntu, but would like to set it up using all the hard drives  for best performance. I have a total of 5 drives installed on my machine.

Any help would be appreciated

---

### Post by ryanhaigh on 2008-03-06
I have personally experimented with Reieserfs (not v4 though) and found no real performance difference, infact it seems faster now that I am all ext3, I have been told that this may be because the kernel doesn't have to convert between filesystems or something. The other thing is that reiserfs caused delays when the fs was checked at startup.

I have also read about XFS being better for dealing with large files. I am waiting for oracles btrfs before changing filesystems again.

---

