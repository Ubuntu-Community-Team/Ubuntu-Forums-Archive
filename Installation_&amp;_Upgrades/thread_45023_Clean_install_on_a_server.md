---
title: "Clean install on a server?"
date: 2005-06-28
forum: Installation &amp; Upgrades
---

### Post by mudshark on 2005-06-28
Greetings,
Kind of a newby question... I got a Compaq server with RAID from my company when we upgraded. All the data is gone but NT Server 4.0 is on it. I do not want to dual -boot but have it ubuntu dedicated. I am new to the server world. Should I just wipe all the drives clean and then stick in my Hoary CD and the instaqllation begins? If this is so, how to sweep the drives on the server? If not, what is the procedure? Thanks for your patience, I am just not too familiar with RAID, partitians, etc.

Thanx

---

### Post by dfghost on 2005-06-28
The answer to first question is yes.  Wipe the drives clean and start anew with ubuntu.  To the second, all you have to do is put the CD in, boot up the machine with it in, setup ubuntu and it should default to wipping the HD.  If it doesn't do the following: when it gets to the partition area select manually partition.  When that comes up, scroll down to your main drive (the first drive probably, not the ones under it and tabbed to the right) and hit the return key.  There should then be an option to reformat and start over with the drive, select that.  Then just do defaults from there and your on your way.  By the way, if it is a RAID HD, then just select the raid option in the partition table.

---

### Post by mudshark on 2005-06-29
Thanks for the info, I will try that. I am not sure if it is a RAID HD. I have not cracked the case but there are four HD's plugged into the front of the box. From what I was told these four drives comprised the RAID but that the main drive was inside the box like a regular pc.

Soooo, when I select the raid option in the partition table during install will this make each drive in the RAID look like just another partition on the main HD or back-ups of the main HD? From what I have read, that is what the RAID is supposed to do.

---

### Post by dfghost on 2005-06-29
I've never really installed a pc with a main RAID HD config, so maybe someone that has can answer that question for you.  Tell me if the install works though.

---

### Post by mudshark on 2005-06-30
Thanks dfghosgt. I am planning to wade into it tomorrow since I have the day off.

---

### Post by mudshark on 2005-07-03
Everything went smoothly - aside from the wife getting a bit miffed at my bringing more toys into the house!

---

