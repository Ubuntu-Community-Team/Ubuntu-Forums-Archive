---
title: "Manually prepare partitions problem."
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by r3bol on 2007-05-06
I'm in the middle of my install process - step 4 of 7 - Manually prepare partitions. 
I want to install on dev/hda2, but I can't seem to proceed with the installation...
[I]Error, No root file system is defined.
Please correct this from the partitioning menu. [/I]
What does this mean and how do I get around it?
note: dev/hda2 has had a previous version of linux on it, which I prepared with GParted (ext3, 20GB). Windows XP is on dev/hda1 so it will be a duel boot.

Thanks.

---

### Post by hessiess on 2007-05-06
create a ext3 partition with / as the mount point. or rename a ext3 partition with/

---

### Post by r3bol on 2007-05-06
Thanks it worked. 
What was all that 'mount point' about? I have installed few linux systems and usually just pick dev/hda(n) to install onto. I noticed quite a few options on mount point - what do the others do?

---

### Post by hessiess on 2007-05-06
im just saying what the install guide i used sed, im new to linux.

the mount point is a blank partition with / as the name, the instaler must look for /

---

