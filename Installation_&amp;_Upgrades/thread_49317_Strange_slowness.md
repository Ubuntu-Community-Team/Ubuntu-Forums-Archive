---
title: "Strange slowness"
date: 2005-07-15
forum: Installation &amp; Upgrades
---

### Post by jsypolt on 2005-07-15
So I'm installing Hoary on an x86 that is a couple of years old. And I set up 2 smallish disks (8gb and 4gb) under LVM and formatted to XFS. LILO won't install (probably cause of XFS right?) so I reboot to change to Reiser. The thing now all of a sudden takes bloody ages to load up and even refresh between installer screens such as when asking for keyboard type, etc. It takes over 30 minutes just to get to the partitioner whereas before it was very quick as one would expect. I thought maybe at first this was because I used XFS but the same thing happens now that I st everything up using Reiser. Any ideas, maybe LVM? Thanks!

---

### Post by jsypolt on 2005-07-15
Well this seems to have 'worked itself out' I let the installer run through again, and 2 hours later after it copied about half of the packages over it all of a sudden started behaving normally <shrug>.

---

