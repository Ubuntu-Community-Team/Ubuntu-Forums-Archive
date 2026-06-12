---
title: "How do I check Windows partition for data loss?"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by tejvenim on 2007-01-11
I didn't run defrag before I resize the windows partition (I'm a newbie so I make silly mistake).

Now I'm worried that there is data loss. Is there a way to check for data loss on the windows partition.

---

### Post by bruenig on 2007-01-11
You can't boot into it?

---

### Post by tejvenim on 2007-01-11
I can boot Windows XP, but I want to check whether there is data loss.

---

### Post by bruenig on 2007-01-12
Boot into xp, check to see if you are missing stuff. Or am I being retarded and not understanding what you mean by data loss.

---

### Post by tejvenim on 2007-01-12
My Windows partition use NTFS filesystem.

A file may be broken up into several chunks, for example a 30MB file is broken up into three chunks, 5MB chunk at the front of the partition, 10MB chunk at the middle of the partition, 15MB chunk at the end of the partition.

So when I shrink the size of the end of the partition, I might accidently delete the 15MB chunk of data which is located at the end of the partition.

I want to check if there are files that have chunks of data located at end of the partition, then these files have data loss.

---

### Post by afternine on 2007-01-12
Just type ckhdsk c: in a command prompt. Do this for every letter you have assigned a disk, ie. d: e: ... It will tell you if the filesystem is OK.

bye

---

