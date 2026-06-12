---
title: "Partitons"
date: 2006-02-24
forum: Installation &amp; Upgrades
---

### Post by arckeda on 2006-02-24
Ok i have a Fat32 partition on a hd that is my backups, and I have a NTFS on a different hd that is my windows xp.  Whenever i try to resize my NTFS it doesnt do anything, i tried the thing on install cd and gparted on live cd, when i diskdefragment my NTFS it says it has unmovable files on it, is that the problem?

---

### Post by adrenaline on 2006-02-24
Interesting...on my laptop I had disabled system restore (apparently creates unmovable files) and then booted into safe mode to defrag xp home.  After that gparted worked like a charm.

---

### Post by arckeda on 2006-02-24
Uh I dont like "disabled system restore" can i still restore if i foobar up? and why did you need to be in safe mode?

---

### Post by adrenaline on 2006-02-24
Once it's disabled I'm pretty sure it deletes the restore points for good.  I don't know if being in safe mode matters but I usually defrag in safe mode just so I don't have as many processes running.

---

### Post by arckeda on 2006-02-24
So if i get red of  my system restore and teh partitions screw up im screwed?

---

### Post by arckeda on 2006-02-24
OH wait do you mean system restore or system recovery!?

---

### Post by arckeda on 2006-02-24
Cause i have an extra harddrive for system recovery so if i wipe my NTFS i will be ok...

---

### Post by adrenaline on 2006-02-24
Honestly, I don't feel like I have enough expertise to tell you exactly what you should do.  All I know is that it worked for me and the process was completely painless.  Hopefully someone else will provide some insight.

Best of luck!

---

### Post by arckeda on 2006-02-24
Man, I turned of restore and there are still unmovable files on my drive...

---

### Post by adrenaline on 2006-02-24
I don't think you can get rid of all the unmovable files.  How much free space is on your drive and how much are you planning on slicing off for your new partition?

---

### Post by arckeda on 2006-02-24
On my drive i have 177GB of free space on my NTSF partition, i want to slice of 8GB for a new fat32 and 20GB for swap and ext3 so i will have
1 NTSF 
2 Fat32
1 Swap&ext3

---

### Post by adrenaline on 2006-02-24
Oh wow!  You have plenty of room.  If you have defragmented it already, I can't see why resizing wouldn't work...

---

### Post by arckeda on 2006-02-24
It just wont resize, i thinks its this unmovable files, cause i can resize my FAT32 just fine...

---

### Post by arckeda on 2006-02-24
OH, i have 1 hd and 2 partitons not 2 hds...

---

