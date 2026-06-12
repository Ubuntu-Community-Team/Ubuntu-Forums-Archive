---
title: "Automatic partitioning question"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by mczonie on 2010-01-01
I want to install a dual boot on my windows machine and found [_this page_]("https://help.ubuntu.com/community/WindowsDualBoot"). Under "Automatic partitioning" it says:

> 1. Choose the First Option (It should be something like: "Resize IDE1 master, partition #1 (hda1) and use freed space").
2. Specify the size of the new partition as a percentage of your entire hard disk.
3. Click on "Forward".
4. continue to Finishing Ubuntu Installation


So far, so good, but there's nothing there indicating exactly how big I should make the new partition. Any advice? TIA. 

P.S. The version of windows I have is XP, if that matters.

---

### Post by Old_Grey_Wolf on 2010-01-01
Did you follow the preceding steps to shrink the Windows partition?

Do you know how much of your disk Windows is using?

You could give Ubuntu 10 GB, then install it. Later, you can resize the partitions.

---

### Post by mczonie on 2010-01-01
> Did you follow the preceding steps to shrink the Windows partition?

I defragmented. 

> Do you know how much of your disk Windows is using?

I just checked my memorey and I have lots to spare, but I don't remember exactly how much. I know there's at least 10 GB there. 

> You could give Ubuntu 10 GB, then install it. Later, you can resize the partitions.

What are the advantages and disadvantages of using more than 10 GB for your partition?

---

### Post by Old_Grey_Wolf on 2010-01-01
> **mczonie said:**
> 
What are the advantages and disadvantages of using more than 10 GB for your partition?

Advantage is that you can store more user data files; such as, music and movie files.

---

### Post by raymondh on 2010-01-01
Hello Mczonie,

To use the 'freed space', you need to create free space (unallocated) outside the windows partition.  Following the link you provided (and the question of 'old grey') whether you shrank windows... XP does not have the ability to shrink.

[See this post]("http://ubuntuforums.org/showpost.php?p=8585386&postcount=8").  Similar to yours except that the OP was installing 9.04.

Post back if you need clarifications.  Here's the whole thread

[http://ubuntuforums.org/showthread.php?t=1367248](http://ubuntuforums.org/showthread.php?t=1367248)

---

### Post by mczonie on 2010-01-01
> **Old_Gray_Wolf said:**
> Advantage is that you can store more user data files; such as, music and movie files.

Maybe I'll just split it 50/50 then. 50% for windows and 50% for Linux. Sound like a good idea?

---

### Post by Old_Grey_Wolf on 2010-01-01
> **mczonie said:**
> Maybe I'll just split it 50/50 then. 50% for windows and 50% for Linux. Sound like a good idea?

Sound like a good idea unless Windows uses more that 40% if the disk space.

---

