---
title: "XFS: input/output error"
date: 2005-08-12
forum: Installation &amp; Upgrades
---

### Post by tom-ubuntu on 2005-08-12
Hi Ubuntu guys

Need your help on another topic: Got an XFS partition (migrated vom FC2 to Ubuntu) and got a problem with copying a file:

```
cp: reading `file.bak': Input/output error
``` 

I checked the disk with xfs_check and also with xfs_repair; none of them found a problem. Disk is not full. 

Any other suggestion? I am a little bit worried about a hardware failure....

Any help appreciated!
Joe

---

### Post by nad on 2005-08-14
How full is the disk? If it is 95%, it is effectively full.

You could install smartmontools to monitor and check your drive for physical and electronic problems.

---

### Post by tom-ubuntu on 2005-08-14
Finally an answer, thank you! No, it is just 69%. I will check the smartmontools out, and see, if they find something. 

Will probably migrate to ReiserFS after that, never had any problems with that and using it for a while and on many machines....

---

### Post by coldwiston on 2006-04-12
I'm getting the same error, when attempting to access various directories on my XFS drive. It is the largest disk i own, and I can't afford a new one at the moment!

I fear the errors might be spreading, I have unmounted it for now, want to disconnect it physically until i get a replacement, if it is indeed dying. Though I want to be sure.

I ran "smartctl -l error /dev/hdb" and got this:

```

smartctl version 5.32 Copyright (C) 2002-4 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Error Log Version: 1
Warning: ATA error count 28563 inconsistent with error log pointer 5

ATA Error Count: 28563 (device log contains only the most recent five errors)
...
```

Followed by the five error events mentioned (all appear to be from a single access attempt).

xfs_repair fails (with "Input/output error" lol), and xfs_check reports something fishy going on, but it doesnt make any sense to me. Sorry, I dont have the output of these on me, but i can post it later for anyone who wants it.

One (possibly important) point i should mention: I recently installed the 2.6.12-10-k7 linux kernel from the repositories, problems seem to have begun popping up after that. I guess going back to the stock kernel might help, but doubt it :(

---

