---
title: "backing up nightly to make a bootable backup (if possible)"
date: 2012-09-11
forum: Installation &amp; Upgrades
---

### Post by allenbina on 2012-09-11
Hey friends,

The hard drive of my trusty home server just died and when reinstalling I decided to try something new for backup purposes.  

I partitioned my hard drive with the following:

15 gig partition ext4 - used as / (we'll call this MainPart just to be clear)
15 gig partition ext4 - (calling this BackupPart to avoid confusion)
220 gig partition ext4 - auto mounted as /share (to be shared on the network)

My goal was to be able to backup everything from MainPart to BackupPart (exact same size) so in the case that I want to roll back changes, I can.  I know this can be done using clonezilla, but I don't know if there is a way to do this automatically, and without shutting down and booting from another disk.  If I do a weekly rsync from MainPart to BackupPart, and something goes wrong, will I be able to boot into a live disk and copy everything back and get a restored os?  

Ultimately I'm looking for a tool that can backup real time or in some sort of increment (weekly would be ideal) so that if I mess anything up, I can roll back to an old version.

cheers

---

