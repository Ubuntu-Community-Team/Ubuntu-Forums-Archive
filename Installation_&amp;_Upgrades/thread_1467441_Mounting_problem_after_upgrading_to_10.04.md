---
title: "Mounting problem after upgrading to 10.04"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by magicdanw on 2010-04-30
I just upgraded to Ubuntu 10.04 LTS, and receive an error upon booting:

"An error occurred while mounting static"

I cannot find anything about this error anywhere online - Google has zero results for that phrase in quotes.

Pressing M to drop to a console, I see

"Filesystem check or mount failed."

However, the main filesystem seems to have mounted quite fine, since I can access it all via the console.

Any ideas?  Please let me know if you have any thoughts, if any particular log file contents would be useful, etc.

Thanks for any help you can offer :)

---

### Post by magicdanw on 2010-04-30
Update: I found the Ubuntu recovery mode, and here is the final output:

fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 439597/9404416 files, 33083900/37594100 blocks
mount: unknown filesystem type 'file'
mountall: mount static [583] terminated with status 32
mountall: Filesystem could not be mounted: static

This is kind of worrisome - filesystem type 'file'???  However, the filesystem does seem to mount okay, something is just blocking along the startup process...

Also, if I try to ignore the problem and run startx, it reports:

(EE) Failed to load module "dri" (module does not exist, 0)
(EE) Can't load FireGL DRM library (libfglrxdrm.so).

Some kind of graphics driver problem too?  Oh dear...

---

### Post by LinuXGo on 2010-05-03
Greeting, it seemed that you had stumbled on the issue that foremost appears as severly annoying and through the percentage toward the users upgrading to Lucid Lynx 10.04,they may discover that when they restart, they discover the system can't seem to mount the disk.
 
Sadly, I was one of those victims that fell on the pool however I believe that there's a way to resolve this even though my experience with this issue still hasn't been resolved. I've done some research and it appears that the disk need to be checked unmounted, do not operate the fsck command with the disk mount. As the warning has stated that it'll jar some real damage toward the drive.
 
The most safe way is to reboot checking the drive for any errors; touch /forcefsck or boot into live CD and enter Gparted to check on the selected partition (which my computer isn't able to accomplish).
 
Best of Luck.

---

### Post by gojan on 2010-07-04
I had the same problem, everything mounted perfectly but I was receiving "an error occured while mounting static" It turned out I mistakenly erased # from the first line of fstab.

---

