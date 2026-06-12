---
title: "Xubuntu 15.10 installation dvd hangs"
date: 2015-10-23
forum: Installation &amp; Upgrades
---

### Post by egeezer on 2015-10-23
The GUI installation process goes smoothly to the point where it is formatting the partition, but hangs there.  The drop-down terminal record shows Started cleanup of temp directories, but hangs there for 15 minutes, at which time I lost faith that it is behaving properly and came over here to see if anyone else suffers the same thing.

md5sum of the downloaded iso checked out, all starts fine, then hangs.  Anyone else have this problem or a solution?

TIA for answers!

---

### Post by frank3922 on 2015-10-23
I had the exact same problem with xbuntu, Ubuntu Mate and Kubuntu!! no idea what the problem was so I'm Back to Linux Lite!

---

### Post by kansasnoob on 2015-10-23
Possibly this bug:

[https://bugs.launchpad.net/ubuntu/+source/partman-ext3/+bug/1361951](https://bugs.launchpad.net/ubuntu/+source/partman-ext3/+bug/1361951)

Jump to [comment #51]("https://bugs.launchpad.net/ubuntu/+source/partman-ext3/+bug/1361951/comments/51") for my most recent summary of the freeze behavior.

---

### Post by egeezer on 2015-10-24
Hey, it finally worked!  The suggestion I took was to use Gparted from a different partition to format as ext4 the partition I had deleted to use for installing.  In the "Something else" partitioner I unmarked the format checkbox, made / the "Use as", and the previously frozen install went perfectly.

So the magic fix for me was pre-formatting.  THANKS again!

---

