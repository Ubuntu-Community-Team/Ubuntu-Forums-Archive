---
title: "upgrade aborted"
date: 2018-11-20
forum: Installation &amp; Upgrades
---

### Post by silvain-dupertuis on 2018-11-20
I have Ubuntu 16.04 and wanted to upgrade to 18.04.
Whatever the method (sudo do-release-upgrade or graphic interface), I end up with a message about insufficient space on disk, which is not the case, as I have now 70 Go of space - I have a double-boot installation Windows 10/Ubuntu 16.04, a i7 processor and 1 TB harddisk.
  	 	 	 	  *The upgrade has aborted. The upgrade needs a total of 5'345 M free *
*space on disk '/var/cache/apt/archives'. Please free at least an *
[I]additional 1'050 M of disk space on '/var/cache/apt/archives'. 

Any idea of the reason for this strange message and how to solve the problem?
[/I]

---

### Post by oldos2er on 2018-11-20
Can you please post the output of  ```
df -h 
```?

---

### Post by Dennis N on 2018-11-20
Is /var on a separate partition? That might explain it. I've gotten the message several times when space on / is low so it's not unusual. Just create more space by removing some files, or adding to the available space by expanding the partition (or LV) if it can be done.

---

