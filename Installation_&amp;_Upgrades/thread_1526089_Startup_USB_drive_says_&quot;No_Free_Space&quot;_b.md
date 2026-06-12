---
title: "Startup USB drive says &quot;No Free Space&quot; but won't delete anything!"
date: 2010-07-07
forum: Installation &amp; Upgrades
---

### Post by quixote on 2010-07-07
I have a 2GB USB thumbdrive which Startup Disk Creator turned into a LiveUSB.  I reserved 128MB for persistent memory.  Then I went and filled it all up by adding the multiverse repository.  When it went to reload repos, it filled up all the available space and that was that.  :rolleyes:

The trash is empty, and I've deleted files, bypassing trash.  But the problem persists.  I thought apt stored its info in /var/cache/apt, but that's just a 60K directory or so, so I don't see how it could be the problem.  I gather aufs is the persistent memory filesystem, so I tried deleting that on the assumption the system might recreate a new empty one, but no luck.  "Sudo rm /aufs" told me it wasn't a directory, and "sudo rm -rf /aufs" didn't return any errors but the drive full problem persists.

Is there some elegant way I can dump all my modifications to the LiveUSB so I have my 128MB back?  I know the simplest thing is probably to start over and reinstall, but it would be useful to know if there's some way to recover from this kind of mistake.

---

