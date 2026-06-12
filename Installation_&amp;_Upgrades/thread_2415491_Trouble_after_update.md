---
title: "Trouble after update"
date: 2019-03-26
forum: Installation &amp; Upgrades
---

### Post by jazcabbage on 2019-03-26
I was doing a fresh install on a new hard drive that went with out issues. I installed all the updates, reboot and I get an error screen. Tried reinstalling and updating in terminal, rebooted and same error. I’m not quite sure how to correct this. 

“( /dev/sda2 contains a file system with errors, check forced. 
Inodes that were part of a corrupted orphan linked list found.

/dev/sda2: UNEXPECTED INCONSISTENCY: RUN fav MANUALLY. (I.e., without -a or -p options)
fsck exited with status code 4
the root filesystem on /dev/sda2 requires a manual fsck )”

---

### Post by houstonbofh on 2019-03-27
Your hard drive may be failing.  Look at it with a SMART capable rescue disk.  If it shows good, something corrupted your install.  Try reinstalling since you have no data there yet.

---

### Post by jazcabbage on 2019-03-28
I can install and boot/reboot with out issues as long as I don’t update. The second I installed updates it hang up on rebooting.

---

### Post by houstonbofh on 2019-03-29
If the update is written to the part of the drive that is failing...  What does SMART say?

---

