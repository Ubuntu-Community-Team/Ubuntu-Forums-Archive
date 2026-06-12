---
title: "Problem partitioning Ubuntu"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by nickd916 on 2007-03-07
Ok so I am new to Linux and want to make my laptop a dual boot (Ubuntu/XP) So i set up my keyboard and time and aks about the partioning.  I move the slider to about 20gb and click next.  2o minutes later it is still in the same place.  How do i move on to the next step?

---

### Post by mikewhatever on 2007-03-07
Have you defragmented and ran CHKDISK from Windows? Depending on the number of files GParted partition manager needs to move, the process can take longer then 2 minutes, or was that 20?

---

### Post by nickd916 on 2007-03-07
it was twenty :(  So i should go inton XP and defragment my disk?

---

### Post by mikewhatever on 2007-03-07
> **nickd916 said:**
> it was twenty :(  So i should go inton XP and defragment my disk?
Yes, certainly, and several times. Defragmentation in Windows will move the files closer to the beginning of the partition, thus making it easier to shrink it from its end. Don't forget the CHKDSK check.

---

### Post by nickd916 on 2007-03-07
Now i keep getting that blue screen when i try to load windows..even in safe mode.  would booting from an XP disc help?

---

### Post by louieb on 2007-03-07
I hope you had a backup or no important data on the drive. Its bad news that you stopped in the middle of the partition resizing.  You may be able to fix XP with the XP CD. Do a forum search on fixmbr and fixboot. These are two commands you can run from the recovery console of the XP CD. If that doesn't work your data may still be recoverable using a live CD and a USB memory stick. 
If you need to use a live CD I recommend using Knoppix or Puppy both are easier  than Ubuntu to use for data recovery.

Plenty of us have done that including me. The one thing I do now is backup.
Experience is something you get after you need it.

---

### Post by nickd916 on 2007-03-13
Alright i fixed the blue screen part...now i just need help on the step where i have to partition.  How long should it take to make the partition automatically.  It takes for ever so i just end up cancelling it.

---

### Post by n8oay on 2007-03-13
This response applies to *ALL* operating systems...

Depending on the size of the original partition, and regardless of the partitioning app that you are using, it could take minutes or hours. I used Acronis Disk Director
[http://www.acronis.com/homecomputing/products/diskdirector/](http://www.acronis.com/homecomputing/products/diskdirector/) 
to resize a single partition on a 120gb drive that contained about 60gb of files. The resize to 80gb partition took, IIRC, about 4 hours. If you need to maintain constant usability of the computer, start the resizing process before you go to bed, and it will be done when get up the next morning. I am guessing that the process will take close to the same amount of time regardless of what partitioning app you use (QTparted, Acronis, Partition Magic, etc.).

---

### Post by Skidpad on 2007-03-13
I had a similar installation problem on my laptop: **[Clicky here](http://www.ubuntuforums.org/showthread.php?t=327923)**
Post #10 describes my solution.  Read the short thread and see if it helps you.  :)

---

### Post by nickd916 on 2007-03-14
alright, I'll try that because I let it automatically do it for at least 15 hours and it's still working.

---

### Post by nickd916 on 2007-03-15
Alright i think i got everything set and in order.  I just need help resizing "/dev/hda1" or whatever that is.  I try to make it smaller but when i got to the next step it says i cannot resize it.  I have only used like 48% of my hard drive.  Also it is defragmented.  there is just one set of contiguous files that are not on the left when i defragment it...could that be the problem?
This is what it looks like when i defragment and clcik analyze (It is all blue)


[IIIIIIIIIIIIIIIIIIIIIII                                        III     ]

                                                                ^ could that be the problem?  hope not cuz I cant move it to the left
Thanks for any help
 Nick

---

