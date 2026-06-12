---
title: "Trying to install, but installer complains!"
date: 2006-09-17
forum: Installation &amp; Upgrades
---

### Post by squimmy on 2006-09-17
Hello, I'm trying to install ubuntu. So I booted it from the cd, selected start in safe graphics mode (normal doesn't work) and went to install.

I already have the partition's set up, 2 for windows (hda1 and hda 2) and 2 for linux(hda 3 and hda 4). The installer initially confused me, forcing me to select "Manually edit partition tables", which is pretty intimidating for a newbie.

Anyway, I got the section where it asks me to choose my mount points and made sure hda1 and hda2's "reformat" checkbox was **un**selected and that hda3 and hda4's "reformat" checkbox was selected. I then hit install.

About the seconds later, I got a message along the lines of

"FAT partition has uncorrected errors. Continue?". I then chickened out and exited.

now, hda1 is the only FAT partition, so it had to be that one.

What I don't understand, is:

A) What that means? It is the backup partition that came with the computer, I didn't create it, but I'd still like it kept intact.

B) Why it complained. I don't want ubuntu to touch,look or even think about those partitions. It should leave it alone, so why did it complain about it?





What this all really boils down to, is should I of clicked continue? Obviously I'm trying to dual boot, so I want windows to stay intact. If I do it again, and click continue when I see that message, will I lose windows?



Thanks for any help.

---

### Post by foolsh on 2006-09-17
i get stange errors on that screen too aslong as you not resizing the partition i see no harm in clicking continue but if you are then stop go back to windows and run scan disk and defrag maybe defrag a few times i find it never gets everthing right the first time

---

### Post by kerry_s on 2006-09-17
sounds like you didn't select a mount point. do the manually edit again and click the top one to select the file system(ext2,ext3,reiserfs.xfs,jfs) it has to be a linux filesystem than on the next line where it says "mount" select "/" which is a root partion(you only need 1, but it can be split farther) just use 1 partion for now it's much simpler. Then choose "done setting up" and finally finish partioning.

---

### Post by squimmy on 2006-09-19
Does ubuntu make changes to the hard drive partitions which are not selected for reformat?



If not, then there's no risk with going ahead is there?

---

### Post by squimmy on 2006-09-27
bump

---

